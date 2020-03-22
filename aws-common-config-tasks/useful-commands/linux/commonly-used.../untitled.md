---
description: 'https://linuxize.com/post/basic-linux-commands/'
---

# Basic Linux Commands

New Linux converts coming from the Windows world may find working with the command line to be somewhat intimidating. However, it’s not that difficult to use. All you need to get started with the command line is to learn a few basic commands.

While most Linux distributions are user-friendly and come with an easy to use graphical interface, knowing how to use the command line can be very useful. The command line gives you more power over your system and access to features that are not available through a graphical interface.

In this article, we’ll go through some of the most common Linux commands that are used on a daily basis by the Linux system administrators.

## Getting Information About the Command [\#](https://linuxize.com/post/basic-linux-commands/#getting-information-about-the-command) <a id="getting-information-about-the-command"></a>

Memorizing command options is usually not necessary and may be a waste of time. Usually, if you are not using the command frequently, you can easily forget its options.

Most commands have a `--help` option which prints a short message about how to use the command and exits:

### The `man` command [\#](https://linuxize.com/post/basic-linux-commands/#the-man-command) <a id="the-man-command"></a>

Almost all Linux commands are distributed together with man pages. A man or manual page is a form of documentation that explains what the command does, examples of how you run the command, and what arguments it accepts.

The `man` command is used to display the manual page of a given command.

For example, to open the man page of the, `cd` command you would type:

```text
man cd
```

To navigate the man pages, use the `Arrow`, `Page Up` and `Page Down` keys. You can also press `Enter` key to move one line at a time, the `Space` bar to move to the next screen, and the `b` key to go one screen back. To exit the man page, press the `q` key.

## Navigating the File System [\#](https://linuxize.com/post/basic-linux-commands/#navigating-the-file-system) <a id="navigating-the-file-system"></a>

In Linux, every file and directory is under the root directory, which is the first or top-most directory in the directory tree. The root directory is referred to by a single leading slash `/`.

When navigating the file system on operating on files, you can use either the absolute or the relative path to the resource.

The absolute or full path starts from the system root `/`, and the relative path starts from your current directory.

### Current Working Directory \(`pwd` command\) [\#](https://linuxize.com/post/basic-linux-commands/#current-working-directory-pwd-command) <a id="current-working-directory-pwd-command"></a>

The current working directory is the directory in which the user is currently working in. Each time you interact with your command prompt, you are working within a directory.

Use the [`pwd`](https://linuxize.com/post/current-working-directory/) command to find out what directory you are currently in:

```text
pwd
```

The command displays the path of your current working directory:

```text
/home/linuxize
```

### Changing directory \(`cd` command\) [\#](https://linuxize.com/post/basic-linux-commands/#changing-directory-cd-command) <a id="changing-directory-cd-command"></a>

The [`cd`](https://linuxize.com/post/linux-cd-command/) \(“change directory”\) command is used to change the current working directory in Linux and other Unix-like operating systems.

When used without any argument, `cd` will take you to your home directory:

```text
cd
```

To change to a directory, you can use its absolute or relative path name.

Assuming that the directory `Downloads` exists in the directory from which you run the command, you can navigate to it by using the relative path to the directory:

```text
cd Downloads
```

You can also navigate to a directory by using its absolute path:

```text
cd /home/linuxize/Downloads
```

Two dots \(`..`\), one after the other, are representing the parent directory or, in other words, the directory immediately above the current one.

Suppose you are currently in the `/usr/local/share` directory, to switch to the `/usr/local` directory \(one level up from the current directory\), you would type:

```text
cd ../
```

To move two levels up use:

```text
cd ../../
```

To change back to the previous working directory, use the dash \(`-`\) character as an argument:

```text
cd -
```

If the directory you want to change to has spaces in its name, you should either surround the path with quotes or use the backslash \(\) character to escape the space:

```text
cd Dir\ name\ with\ space
```

## Working with Files and Directories [\#](https://linuxize.com/post/basic-linux-commands/#working-with-files-and-directories) <a id="working-with-files-and-directories"></a>

### Listing directory contents \(`ls` command\) [\#](https://linuxize.com/post/basic-linux-commands/#listing-directory-contents-ls-command) <a id="listing-directory-contents-ls-command"></a>

The [`ls`](https://linuxize.com/post/how-to-list-files-in-linux-using-the-ls-command/) command is used to list information about files and directories within a directory.

When used with no options and arguments, `ls` displays a list in alphabetical order of the names of all files in the current working directory:

```text
ls
```

To list files in a specific directory, pass the path to the directory as an argument:

```text
ls /usr
```

The default output of the `ls` command shows only the names of the files and directories. Use the `-l` to print files in a long listing format:

```text
ls -l /etc/hosts
```

The output includes the file type, permissions, number of hard links, owner, group, size, date, and filename:

```text
-rw-r--r-- 1 root root 337 Oct  4 11:31 /etc/hosts
```

The `ls` command doesn’t list the hidden files by default. A hidden file is any file that begins with a period \(`.`\).

To display all files including the hidden files, use the `-a` option:

```text
ls -a ~/
```

### Displaying file contents \(`cat` command\) [\#](https://linuxize.com/post/basic-linux-commands/#displaying-file-contents-cat-command) <a id="displaying-file-contents-cat-command"></a>

The [`cat`](https://linuxize.com/post/linux-cat-command/) command is used to print the contents of one or more files and to merge \(concatenate\) files by appending the contents of one file to the end of another file.

To display the contents of a file on the screen, pass the file name to `cat` as an argument:

```text
cat /etc/hosts
```

### Creating files \(`touch` command\) [\#](https://linuxize.com/post/basic-linux-commands/#creating-files-touch-command) <a id="creating-files-touch-command"></a>

The [`touch`](https://linuxize.com/post/linux-touch-command/) command is used to update the timestamps on existing files and directories as well as to create new, empty files.

To [create a file](https://linuxize.com/post/create-a-file-in-linux/), specify the file name as an argument:

```text
touch file.txt
```

If the file already exists, `touch` will change the file last access and modification times to the current time.

### Creating directories \(`mkdir` command\) [\#](https://linuxize.com/post/basic-linux-commands/#creating-directories-mkdir-command) <a id="creating-directories-mkdir-command"></a>

In Linux, you can create new directories \(also known as folders\) using the [`mkdir`](https://linuxize.com/post/how-to-create-directories-in-linux-with-the-mkdir-command/) command.

To create a directory, pass the name of the directory as the argument to the command:

```text
mkdir /tmp/newdirectory
```

`mkdir` can take one or more directory names as its arguments.

When providing only the directory name, without the full path, it will be created in the current working directory.

To create parent directories use the `-p` option:

```text
mkdir -p Projects/linuxize.com/src/assets/images
```

The command above creates the whole directory structure.

When `mkdir` is invoked with the `-p` option, it creates the directory only if it doesn’t exist.

### Creating symbolic links \(`ln` command\) [\#](https://linuxize.com/post/basic-linux-commands/#creating-symbolic-links-ln-command) <a id="creating-symbolic-links-ln-command"></a>

A symbolic link \(or symlink\) is a special type of file that points to another file or directory.

To create a symbolic link to a given file, use the [`ln`](https://linuxize.com/post/how-to-create-symbolic-links-in-linux-using-the-ln-command/) command with the `-s` option, the name of the file as the first argument and the name of the symbolic link as the second argument:

```text
ln -s source_file symbolic_link
```

If only one file is given as an argument `ln` creates a link to that file in the current working directory with the same name as the file it points to.

### Removing files and directories \(`rm` command\) [\#](https://linuxize.com/post/basic-linux-commands/#removing-files-and-directories-rm-command) <a id="removing-files-and-directories-rm-command"></a>

To remove files and directories use the [`rm`](https://linuxize.com/post/rm-command-in-linux/) command.

By default, when executed without any option, `rm` doesn’t remove directories. It also doesn’t prompt the user for whether to proceed with the removal of the given files.

To delete a file or a symlink, use the `rm` command followed by the file name as an argument:

```text
rm file.txt
```

`rm` accepts one or more file or directory names as its arguments.

The `-i` option tells `rm` to prompt the user for each given file before removing it:

```text
rm -i file.txt
```

```text
rm: remove regular empty file 'file.txt'? 
```

Use the `-d` option to remove one or more empty directories:

```text
rm -d dirname
```

To remove non-empty directories and all the files within them recursively, use the `-r` \(recursive\) option:

```text
rm -rf dirname
```

The `-f` option tells `rm` never to prompt the user and to ignore nonexistent files and arguments.

### Copying files and directories \(`cp` command\) [\#](https://linuxize.com/post/basic-linux-commands/#copying-files-and-directories-cp-command) <a id="copying-files-and-directories-cp-command"></a>

The [`cp`](https://linuxize.com/post/rm-command-in-linux/) command allows you to copy files and directories.

To copy a file in the current working directory, use the source file as a first argument and the new file as the second:

```text
cp file file_backup
```

To copy a file to another directory, specify the absolute or the relative path to the destination directory. When only the directory name is specified as a destination, the copied file will have the same name as the original file.

```text
cp file.txt /backup
```

By default, if the destination file exists, it will be overwritten.

To copy a directory, including all its files and subdirectories, use the `-R` or `-r` option:

```text
cp -R Pictures /opt/backup
```

### Moving and renaming files and directories \(`mv` command\) [\#](https://linuxize.com/post/basic-linux-commands/#moving-and-renaming-files-and-directories-mv-command) <a id="moving-and-renaming-files-and-directories-mv-command"></a>

The [`mv`](https://linuxize.com/post/how-to-move-files-in-linux-with-mv-command/) command \(short from move\) is used to rename and move and files and directories from one location to another.

For example to move a file to a directory you would run:

```text
mv file.txt /tmp
```

To rename a file you need to specify the destination file name:

```text
mv file.txt file1.txt
```

The syntax for moving directories is the same as when moving files.

To move multiple files and directories at once, specify the destination directory as the last argument:

```text
mv file.tx1 file1.txt /tmp
```

## Installing and Removing Packages [\#](https://linuxize.com/post/basic-linux-commands/#installing-and-removing-packages) <a id="installing-and-removing-packages"></a>

A package manager is a tool that allows you to install, update, remove, and otherwise manage distro-specific software packages.

Different Linux distributions have different package managers and package formats.

Only root or user with sudo privileges can install and remove packages.

### Ubuntu and Debian \(`apt` command\) [\#](https://linuxize.com/post/basic-linux-commands/#ubuntu-and-debian-apt-command) <a id="ubuntu-and-debian-apt-command"></a>

Advanced Package Tool or APT is a package management system used by Debian-based distributions.

There are several command-line package management tools in Debian distributions with [`apt`](https://linuxize.com/post/how-to-use-apt-command/) and `apt-get` being the most used ones.

Before installing a new package first, you need to update the APT package index:

```text
apt update
```

The APT index is a database that holds records of available packages from the repositories enabled in your system.

To upgrade the installed packages to their latest versions run:

```text
apt upgrade
```

Installing packages is as simple as running:

```text
apt install package_name
```

To [remove an installed package](https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/), enter:

```text
apt remove package_name
```

### CentOS and Fedora \(`dnf` command\) [\#](https://linuxize.com/post/basic-linux-commands/#centos-and-fedora-dnf-command) <a id="centos-and-fedora-dnf-command"></a>

RPM is a powerful package management system used by Red Hat Linux and its derivatives such as CentOS and Fedora. RPM also refers to the [`rpm`](https://linuxize.com/post/rpm-command-in-linux/) command and `.rpm` file format.

To [install a new package](https://linuxize.com/post/how-to-install-rpm-packages-on-centos-linux/) on Red Hat based distributions, you can use either `yum` or `dnf` commands:

```text
dnf install package_name
```

Starting from CentOS 8 `dnf` replaced `yum` as the default package manager. `dnf` is backward compatible with `yum`.

To upgrade the installed packages to their latest versions, type:

```text
dnf update
```

Removing packages is as simple as:

```text
dnf remove package_name
```

## File Ownership and Permissions [\#](https://linuxize.com/post/basic-linux-commands/#file-ownership-and-permissions) <a id="file-ownership-and-permissions"></a>

In Linux, access to the files is managed through the file permissions, attributes, and ownership. This ensures that only authorized users and processes can access files and directories.

In Linux, each file is associated with an owner and a group and assigned with permission access rights for three different classes of users:

* The file owner.
* The group members.
* Everybody else.

There are three permissions types that apply to each class:

* The read permission.
* The write permission.
* The execute permission.

This concept allows you to specify which users are allowed to read the file, write to the file, or execute the file.

To view the file owner and permissions, use the `ls -l` command.

### Changing permissions \(`chmod` command\) [\#](https://linuxize.com/post/basic-linux-commands/#changing-permissions-chmod-command) <a id="changing-permissions-chmod-command"></a>

The [`chmod`](https://linuxize.com/post/chmod-command-in-linux/) command allows you to change the file permissions. It works in two modes, symbolic and numeric.

When using the numeric mode, you can set the permissions for the owner, group, and all others. Each write, read, and execute permissions have the following number value:

* `r` \(read\) = 4
* `w` \(write\) = 2
* `x` \(execute\) = 1
* no permissions = 0

The permissions number of a specific user class is represented by the sum of the values of the permissions for that group.

For example, to give the file’s owner read and write permissions and only read permissions to group members and all other users you would run:

```text
chmod 644 filename
```

Only root, the file owner, or user with sudo privileges can change the permissions of a file.

To [recursively](https://linuxize.com/post/chmod-recursive/) operate on all files and directories under a given directory, use the `chmod` command with the -R, \(–recursive\) option:

```text
chmod -R 755 dirname
```

Be extra careful when recursively changing the files’ permissions.

### Changing ownership \(`chown` command\) [\#](https://linuxize.com/post/basic-linux-commands/#changing-ownership-chown-command) <a id="changing-ownership-chown-command"></a>

The [`chown`](https://linuxize.com/post/linux-chown-command/) command allows you to change the user and group ownership of a given file, directory, or symbolic link.

To change the owner of a file, use the `chown` command followed by the user name of the new owner and the target file:

```text
chown username filename
```

To change both the owner and the group of a file invoke the `chown` command followed by the new owner and group separated by a colon \(`:`\) with no intervening spaces and the target file:

```text
chown username:groupname filename
```

Use the `-R` \(`--recursive`\) option, to recursively operate on all files and directories under the given directory:

```text
chown -R username:groupname dirname
```

### Elevate privileges \(`sudo` command\) [\#](https://linuxize.com/post/basic-linux-commands/#elevate-privileges-sudo-command) <a id="elevate-privileges-sudo-command"></a>

The [`sudo`](https://linuxize.com/post/sudo-command-in-linux/) command allows you to run programs as another user, by default the root user. If you spend a lot of time on the command line, `sudo` is one of the commands that you will use quite frequently.

Using `sudo` instead of login in as root is more secure because you can grant limited administrative privileges to individual users without them knowing the root password.

To use `sudo`, simply prefix the command with `sudo`:

```text
sudo command
```

## Managing Users and Groups [\#](https://linuxize.com/post/basic-linux-commands/#managing-users-and-groups) <a id="managing-users-and-groups"></a>

Linux is a multi-user system, which means that more than one person can interact with the same system at the same time. Groups are used to organize and administer user accounts. The primary purpose of groups is to define a set of privileges such as reading, writing, or executing permission for a given resource that can be shared among the users within the group.

### Creating users \(`useradd` and `passwd` Commands\) [\#](https://linuxize.com/post/basic-linux-commands/#creating-users-useradd-and-passwd-commands) <a id="creating-users-useradd-and-passwd-commands"></a>

The [`useradd`](https://linuxize.com/post/how-to-uninstall-software-packages-on-ubuntu/) command allows you can create new users.

To create a new user account use the `useradd` command followed by the username:

```text
useradd newuser
```

Once the user is created, set the user password by running the [`passwd`](https://linuxize.com/post/how-to-change-user-password-in-linux/) command:

```text
passwd newuser
```

### Removing users \(`userdel` Command\) [\#](https://linuxize.com/post/basic-linux-commands/#removing-users-userdel-command) <a id="removing-users-userdel-command"></a>

In Linux, you can delete a user account using the [`userdel`](https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/) command.

To delete a user account named pass the user name to the `userdel` command:

```text
userdel newuser
```

Use the `-r` \(–remove\) option to remove the user’s home directory and mail spool:

```text
userdel -r newuser
```

### Managing groups \(`groupadd` and `groupdel` Command\) [\#](https://linuxize.com/post/basic-linux-commands/#managing-groups-groupadd-and-groupdel-command) <a id="managing-groups-groupadd-and-groupdel-command"></a>

To create a new group use the [`groupadd`](https://linuxize.com/post/how-to-create-groups-in-linux/) command followed by the group name:

```text
groupadd mygroup
```

To remove a group use the `groupdel` command with the group name as argument:

```text
groupdel mygroup
```

### Adding users to groups \(`usermod` Command\) [\#](https://linuxize.com/post/basic-linux-commands/#adding-users-to-groups-usermod-command) <a id="adding-users-to-groups-usermod-command"></a>

To add an existing user to a group, use the `usermod` command followed by the `-G` option and the name of the group:

```text
usermod -a -G sudo linuxize
```

## Conclusion [\#](https://linuxize.com/post/basic-linux-commands/#conclusion) <a id="conclusion"></a>

We have covered some of the most used Gnu/Linux commands.

Although you can perform most of the development and system-related tasks using a graphical interface, the command line makes you more productive and able to get more done in less time.

Click on the links on each command to get more information about the command options and usage.

If you have any questions or feedback, feel free to leave a comment.

