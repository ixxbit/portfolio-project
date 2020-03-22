# Linux

![](../../../.gitbook/assets/image%20%2897%29.png)

* Linux cares about capitalization
* FHS: Filesystem Hierarchy Standard 

[https://www.youtube.com/watch?v=HbgzrKJvDRw&t=130s](https://www.youtube.com/watch?v=HbgzrKJvDRw&t=130s)

### 

### /bin and sbin

Both of these folders contain the files that need to be accessible when logging in as single-user mode. when you install a program in linux it's typically not installed in these folders.

* bin - most basic binaries like ls, cat, etc
* sbin - system binary that system admin would use.  This is mostly used with logging in as single-mode as opposed to multi-user mode. single-user special mode logs you in as a root user to do system repair and testing.  network is disabled due to security reasons

### /boot

It contains all the files necesary for the system to boot. You don't want to play around with the content in this folder.

### /dev

Where all the devices live.  Everything is a file. _i.e. sda = sda1, sda2._ Find everything from your webcam to your keyboard. This is typically an area that applications and drivers will access. You share rarely be dabling at. 

### /etc

Where all system-wide configurations are stored such as apt, sources.list. If looking for something that is system-wide this wold be te place to look.

### /lib /lib32 /lib64

These are the libraries. Files that required for applications to perform various functions. _i.e. they are required by the binaries in bin and sbin files._

### /media /mnt

Most distros mount devices in the /media directory. _i.e. usb &gt; media &gt; username &gt; device name._

_Let the OS use the media folder and you use the mnt when manually mounting_

### /opt

The optional folder where manually installed software from vendors reside.  Also install software you created yourself.

### /proc

The proc folder contains sudo files with information about system processes and resources.  _i.e. every process will have a directory here which contains all kinds of information about that process. The kernel creates sudo files with information it that translates representing information about the process -- these are not files on the system.    PID number = /proc/PID number._ These are handy for developers who are writing applications.

**`cat /proc/cpuinfo, /uptime`**

### /root

This is the root user's home folder. unlike a regular user's home folder.  Unlike the user's home folder this one does not contain the typical home directoy folders. You need root permissions to access it. The location of this directory also ensures that the root user always has access to this folder in case the location of the regular user home directories is stored in a separate drive which you cannot access.

### /run

This is a tempfs file system which means that everything runs on RAM. Once the computer restarts everything's gone.  Used for process that start early in the boot procedure to store runtime information that they use to function.

### /snap

Snap packages are store and mainly ran by ubuntu. snap packages are complete self-contained and run differently than other packages

### /srv

Where service directory where server data is stored. If running an ftp or webserver, you would store the files that will be accessed by external users here. **This allows for better security since it's at the root of the drive and also allows you to easily mounting this foler from another hard drive.**

### **/sys**

The system folder has been around for a long time.  This is what communicates with the Kernel.  This directory is created everything it boots up.  So you wouldn't store anything on here. Nothing gets installed here.

### /tmp

This temporary directory regularly saves while you have an open file in case your word processor program crashes. This folder is usually empty when reboot the system. On occassion you may need to manually delete them but will need to log in as the root user on single-mode login.

### /usr

This is the user application space where applications will be installed that are used by the user as opposed to the bin directory that is used by the system and system administrator to perform maintenance.  Also known as the UNIX system resource and any applications installed here are considered non-essential for basic system  operations. **Installed applications will reside in one of the several places such as:**

`usr/bin usr/sbin OR usr/local/bin usr/local/sbin`

with their required libraries stored in:

`usr/lib OR usr/local/lib`

* **Most source code programs will be stored in the `local` folders.**
* **Larger programs will stall themselves into the `usr/share`**
* **Any source code such as the kernel source files and header files will go into the `usr/src`** 

### /var

This variable directory. It contains files and directories that are supposed to grow in size.  The `/var/log` Contains log files for installed applications and system process which will constantly grow in size as you continue using the system. The /var/spool folder contains other things like databases for `mail` and temporary storage for printer queues also known as `spool`



\*\*\*\*









###  



\_\_



### Linux Filesystem Navigation Basics step by step instructions

The below instructions are the absolute minimum a beginner GNU/Linux user needs to master to be able to perform even the simplest tasks on a GNU/Linux command line. Once you learn the basics below, you are ready to move to more advanced [command line](https://linuxconfig.org/linux-commands) topics.   
  


1. When you are working within a shell terminal, you are always operating in a particular directory. To determine which directory you are in, use the [`pwd` command](https://linuxconfig.org/pwd):

   ```text
   student@linuxconfig:$ pwd /usr/local/bin 
   student@linuxconfig:$ cd 
   student@linuxconfig:$ pwd /home/student 
   student@linuxconfig:$ 
   ```

2. Your home directory is the directory you are in when you first open the terminal. To go to your home directory from anywhere, just type [`cd` command](https://linuxconfig.org/cd):

   ```text
   student@linuxconfig:$ pwd
   /usr/local/bin
   student@linuxconfig:$ cd
   student@linuxconfig:$ pwd
   /home/student
   student@linuxconfig:$ 
   ```

3. An absolute path name is one beginning with the `/` character, which signifies the root of the file system tree. Therefore, another way of going to your home directory is:

   ```text
   student@linuxconfig:/etc$ cd /home/student
   student@linuxconfig:$ pwd
   /home/student
   student@linuxconfig:$
   ```

   For more information regarding the Relative vs Absolute path visit our [bash scripting tutorial](https://linuxconfig.org/bash-scripting-tutorial-for-beginners#h8-relative-vs-absolute-path).

4. A relative path is one which starts with the name of a directory connected to the current directory. For example, if you are in the `/usr` directory, then typing only `cd bin` \(without preceding "bin" with "/"\) has the following effect:

   ```text
   student@linuxconfig:$ pwd
   /usr
   student@linuxconfig:$ cd bin
   student@linuxconfig:$ pwd
   /usr/bin
   student@linuxconfig:$
   ```

   and you go to `/usr/bin` rather than `/usr/local/bin` or `/bin`.

5. To go to the directory containing the current working directory \(also called the parent directory\) type:

   ```text
   student@linuxconfig:$ pwd
   /usr/bin
   student@linuxconfig:$ cd ..
   student@linuxconfig:$ pwd
   /usr
   student@linuxconfig:$
   ```

6. The relative pathname of the current working directory is called `.` \(the full stop\). Therefore typing:

   ```text
   student@linuxconfig:$ pwd
   /usr/bin
   student@linuxconfig:$ cd . 
   student@linuxconfig:$ pwd
   /usr/bin
   student@linuxconfig:$
   ```

   does not change the current working directory.

