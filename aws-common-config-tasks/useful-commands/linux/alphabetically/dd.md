# dd

## How dd command works in Linux with examples 

Egidio DocileSystem Administration05 August 2019Contents

* * [1. Software Requirements and Conventions Used](https://linuxconfig.org/how-dd-command-works-in-linux-with-examples#h1-software-requirements-and-conventions-used)
  * [2. Basic usage](https://linuxconfig.org/how-dd-command-works-in-linux-with-examples#h2-basic-usage)
  * [3. Skipping blocks when reading and writing](https://linuxconfig.org/how-dd-command-works-in-linux-with-examples#h3-skipping-blocks-when-reading-and-writing)
  * [4. Compressing the data read by dd](https://linuxconfig.org/how-dd-command-works-in-linux-with-examples#h4-compressing-the-data-read-by-dd)
  * [5. Wiping a block device](https://linuxconfig.org/how-dd-command-works-in-linux-with-examples#h5-wiping-a-block-device)
  * [6. Converting data](https://linuxconfig.org/how-dd-command-works-in-linux-with-examples#h6-converting-data)
  * [7. Conclusions](https://linuxconfig.org/how-dd-command-works-in-linux-with-examples#h7-conclusions)

Dd is a very powerful and useful utility available on Unix and Unix-like operating systems. As stated in its manual, its purpose is to convert and copy files. On Unix and Unix-like operating systems like Linux, almost everything is treated as a file, even block devices: this makes dd useful, among the other things, to clone disks or wipe data. The `dd` utility is available out of the box even in the most minimal installation of all distributions. In this tutorial we will see how to use it and how we can modify its behavior by using some of the most commonly used options to make your [Linux system administration job](https://www.linuxcareers.com/jobs/job-search-results/kw-linux-system-administrator/) easier.**In this tutorial you will learn:**

* How to use dd
* How to modify the program behavior by using some of the most commonly used options

[![dd-manpage](https://linuxconfig.org/images/dd_manpage.png)](https://linuxconfig.org/images/dd_manpage.png)

### Software Requirements and Conventions Used <a id="h1-software-requirements-and-conventions-used"></a>

| Software Requirements and Linux Command Line Conventions |  |
| :--- | :--- |
| Category | Requirements, Conventions or Software Version Used |
| System | Distribution-independent |
| Software | No special software is needed to follow this tutorial except dd |
| Other | Familiarity with the command line interface and redirections |
| Conventions | **\#** - requires given [linux commands](https://linuxconfig.org/linux-commands) to be executed with root privileges either directly as a root user or by use of `sudo` command **$** - requires given [linux commands](https://linuxconfig.org/linux-commands) to be executed as a regular non-privileged user  |

### Basic usage <a id="h2-basic-usage"></a>

The basic syntax of `dd` is very simple. By default the program reads from `standard input` and writes to `standard output`. We can, however, specify alternative `input` and `output` files by using respectively the `if` and `of` [command line options](https://linuxconfig.org/linux-commands#h2-1-command-line-arguments-options-and-parameters). Here dd differs from the vast majority of shell commands, since doesn't use the standard `--option` or `-o`  syntax for options.

**SUBSCRIBE TO NEWSLETTER**  
Subscribe to Linux Career [NEWSLETTER](https://bit.ly/2X5D30q) and receive latest Linux news, jobs, career advice and tutorials. 

Let's see an example of dd usage. One of the most typical use cases for the utility is the backup of the master boot record: the first sector on a legacy `MBR` partitioned system. The length of this sector is usually `512` bytes: it contains the stage 1 of the `grub bootloader` and the disk partition table. Suppose we want to backup the `MBR` of /dev/sda disk, all we have to do is to invoke dd with the following syntax:

```text
$ sudo dd if=/dev/sda bs=512 count=1 of=mbr.img
```

Let's analyze the command above. First of all we prefixed the actual dd invocation with [sudo command](https://linuxconfig.org/sudo-install-usage-and-sudoers-config-file-basics), in order to run the command with administrative privileges. This is needed to access the `/dev/sda` block device. We then invoked dd specifying the input source with the `if` option and the output file with `of`. We also used the `bs` and `count` options to specify respectively the amount of data that should be read at a time, or block size, and the total amount of blocks to read. In this case we could have omitted the `bs` option, since `512` bytes is the default size used by dd. If we run the command above, we will see that it produces the following output:

```text
1+0 records in
1+0 records out
512 bytes copied, 0.000657177 s, 779 kB/s
```

The output above shows us the amount of records read and written, the amount of data copied, the amount of time in which the task was completed and the transfer speed. We now should have a clone of the `MBR` sector, stored in the `mbr.img` file. Obviously the file suffix has no real meaning on Linux, so the use of the ".img" one is completely arbitrary: you may want to use ".dd" to let the filename reflect the command that was used to create the file.

In the example above we use the `bs` option to define both the amount of bytes that should be read and write at a time. To define separately values for the two operations, we can use the `ibs` and `obs` options instead, which set, respectively, the amount of bytes read and written at a time.

### Skipping blocks when reading and writing <a id="h3-skipping-blocks-when-reading-and-writing"></a>

There are cases in we may want to skip a certain amount of block sizes when reading from or writing to a file. In such cases we have to use the `skip` and `seek` options, respectively: they are used to skip the specified blocks of data, at the start of input and at the start of output.

An example of such a situation is when we want to backup/restore the hidden data between the `MBR` and the first partition on the disk, which usually starts at sector `2048`, for alignment reasons.  The `2047` sectors of this area usually contain, on a legacy `MBR` partition setup, the stage 1.5 of the grub bootloader. How can we instruct dd to clone just this area, without including the `MBR`? All we need to do is to use the `skip` option:

```text
$ sudo dd if=/dev/sda of=hidden-data-after-mbr count=2047 skip=1
```

In this case we instructed dd to copy `2047` blocks of `512` bytes from the /dev/sda disk starting from the second one. In the opposite situation, when we want to restore the cloned data and write it back in the same disk zone, we want to use the seek option, which skips the specified number of blocks at beginning of the output:

```text
$ sudo dd if=hidden-data-after-mbr of=/dev/sda seek=1
```

In this case we instructed dd to copy data from the `hidden-data-after-mbr` and to write it on the `/dev/sda` block device starting from the second block.

### Compressing the data read by dd <a id="h4-compressing-the-data-read-by-dd"></a>

As we already said before, one of the most common operations performed with dd is disk cloning. The dd command produces a perfect clone of a disk, since it copies block devices byte by byte, so cloning a 160 GB disk, produces a backup of  the exact same size. When cloning a disk to a file, we can however pipe the data read by dd though compression utilities like `gzip`, to optimize the result and reduce the final file size. Say for example we want to create a clone of the entire /dev/sda block device, we could write:

```text
$ sudo dd if=/dev/sda bs=1M | gzip -c -9 > sda.dd.gz
```

In the example above we instructed dd to read from the /dev/sda device, and we also changed the block size to 1M, which can give us better performance in such situation. We then piped the data, further processing it with the `gzip` program that we invoked with the `-c` \(short for `--to-stdout`\) and `-9` option which instructs the program to use the maximum available compression. Finally, we redirected the output to the "sda.dd.gz" file. By the way, if you want to learn more about `redirections` you can read our [article](https://linuxconfig.org/introduction-to-bash-shell-redirections) on the subject.

### Wiping a block device <a id="h5-wiping-a-block-device"></a>

Another dd use case, is the wiping of a device. There are many situations in which we may need to perform such operation: we may want to sell a disk, and be sure its previous content is completely erased for obvious privacy reasons, or we may want to wipe data before setting up encryption. In the first case it would be enough to overwrite the disk with zeros:

```text
$ sudo dd if=/dev/zero bs=1M of=/dev/sda
```

The above command instructs dd to read from the /dev/zero device which provides null characters and write them to the devices until it is completely filled.

Before setting up an encryption layer on our system we may want to fill the disk with random data instead, to render the its sectors which will contain data indistinguishable from the empty ones and avoid metadata leaks. In this case we want to read data from the `/dev/random` or `/dev/urandom`devices

```text
$ sudo dd if=/dev/urandom bs=1M of=/dev/sda
```

Both the commands will require a significant amount of time to finish, depending on the size and type of the block device in question and the source of random data used, `/dev/random` being slower \(it blocks until it doesn't gather enough environmental noise\), but returning higher quality random data than `/dev/urandom`.

### Converting data <a id="h6-converting-data"></a>

The `conv` options of dd is used to apply data conversions. The options must be provided with a comma separated list of symbols as arguments. Here some of the most used ones:

* noerror - This makes use dd continue even after a read error is encountered;
* notrunc - This option instructs dd to not truncate the output file;
* sync - This option has sense especially when used together with noerror. It instructs dd to pad every input blocks with NULs.

A typical case in which we may want to run dd together with the `conv=sync,noerror` option, is when cloning a disk which contains damaged sectors. In such a case the `noerror` option will make dd continue running even if it a sector cannot be read successfully, and the `sync` option will make so that the amount of data failed to be read its replaced by `NULs`, so that the length of the data is preserved even if the actual data is lost \(since it's not possible to read it\).

### Conclusions <a id="h7-conclusions"></a>

In this tutorial we learned to use the very powerful dd command. We saw some of the typical cases the program is used in, such as disk cloning, and we learn to know its syntax and the more important options we can use to modify its behavior. Since dd is a very powerful utility, it must be used with extreme attention: just by switching the input and output target, one can, in some situations, completely destroy data on a disk.

