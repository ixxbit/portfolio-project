# USB - Mount Points

Do you know “how to use USB memory sticks with Linux”, If you are not sure then this article describes “how to mount USB drive on a Linux system with command line interface”

Universal serial bus, or USB \(also known as Flash drive\), is an electronic communications protocol that is commonly used in computer accessories and other small devices. If you have an up-to-date Linux system and a modern Desktop environment, your device should show up on your desktop, with no need to open a console. There are few important factors which are involved in learning how to mount USB drive with Linux machine.

Following are the step by step instructions to understand further –

### Step 1: Plug-in USB drive to your PC

![](https://www.tutorialspoint.com/assets/questions/media/29814/useb_drive.jpg)

### Step 2 – Detecting USB Drive

After you plug in your USB device to your Linux system USB port, It will add new block device into /dev/ directory. To verify it, use the following command –

```text
$ sudo fdisk -l
```

The sample output should be like this –

```text
Disk /dev/sdb: 15.7 GB, 15664676864 bytes
255 heads, 63 sectors/track, 1904 cylinders, total 30595072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
Device Boot Start End Blocks Id System
/dev/sdb1 * 32 30595071 15297520 c W95 FAT32 (LBA)
```

We can observe from the above result that, device boot, blocks, id and system format are displayed.

### Step 3 – Creating Mount Point

To mount the USB, use the following command –

```text
$ mount /dev/sdb1 /mnt
```

To create a directory in the mounted device, use the following commands –

```text
$ cd /mnt
/mnt$ mkdir john
```

The above command creates a directory called john in USB device.

### Step 4 – Delete a Directory in USB

To delete a directory in USB, use the following command –

```text
/mnt$ rmdir john
```

### Step 5 – Formatting the USB

You should unmount the device first to format the USB device, then use the following command to unmount the device –

```text
$ sudo umount /dev/sdb1
```

Now use either of the commands as per file system based on your requirement. To format a USB drive, users generally prefer **VFAT** or **NTFS** file systems because they can be easily mounted on Windows operating systems and Linux systems.

### Format vs Fat FileSystem

To format USB with vFat File System, use the following command –

```text
$ sudo mkfs.vfat /dev/sdb1
```

### Format NTFS FileSystem

To format a USB Flash Drive with NTFS file system, use the following command –

```text
$ sudo mkfs.ntfs /dev/sdb1
```

### Format EXT4 FileSystem

To format a USB with EXT4 file system, use the following command –

```text
$ sudo mkfs.ext4 /dev/sdb1
```

Congratulations! Now, you know “How to Mount USB Drive in a Linux System?”. We’ll learn more about these types of commands in our next Linux post. Keep reading!

