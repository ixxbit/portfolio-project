---
description: Top 25+
---

# The Essentials



[Blog](https://crunchify.com/)    [Linux and Unix Tutorials](https://crunchify.com/category/linux-unix/)    My Favorite Linux Commands – List of Top 25+ Basic Linux Command ...

## My Favorite Linux Commands – List of Top 25+ Basic Linux Commands and Cheat Sheet

Last Updated on February 25th, 2019 by   App Shah   [ 2 comments](https://crunchify.com/my-favorite-linux-commands-list-of-basic-linux-commands-and-cheat-sheet/#disqus_thread)

* 
![My Favorite Linux Commands - Crunchify Tips](https://cdn.crunchify.com/wp-content/uploads/2017/10/My-Favorite-Linux-Commands-Crunchify-Tips.png)

I’ve been working on [Linux environment](https://crunchify.com/how-to-delete-files-folders-on-windows-machine-from-java/) since very long time and recently explored a lot more commands. In this tutorial we will go over some most commonly used [Linux Commands](https://crunchify.com/bash-sh-how-to-read-a-file-line-by-line-linux-loop-example/) for your handy reference.

Let’s get started.

#### 1. How to Get Linux OS version and System Info?

| root@crunchify:~\# lsb\_release -a No LSB modules are available.Distributor ID: UbuntuDescription: Ubuntu 17.04Release: 17.04Codename: zesty root@crunchify:/opt\# uname -aLinux crunchify 4.9.36-x86\_64-linode85 \#1 SMP Thu Jul 6 15:31:23 UTC 2017 x86\_64 x86\_64 x86\_64 GNU/Linux |
| :--- |


#### 2. How to update your OS to latest version?

apt–get update && apt–get upgrade

#### 3. How to create and extract tar.gz?

| root@crunchify:/tmp/crunchify\# ls -ltratotal 12drwxrwxrwt 10 root root 4096 Oct  6 17:51 ..-rw-r--r--  1 root root    6 Oct  6 17:51 one.txtdrwxr-xr-x  2 root root 4096 Oct  6 17:51 . &lt;!-- Create tar.gz file --&gt; root@crunchify:/tmp/crunchify\# tar -cvf - one.txt \| gzip &gt; crunchify.tar.gzone.txtroot@crunchify:/tmp/crunchify\# ls -ltrtotal 16-rw-r--r-- 1 root root     6 Oct  6 17:51 one.txt-rw-r--r-- 1 root root 10240 Oct  6 17:52 crunchify.tar.gz &lt;!-- Extract tar.gz file --&gt; root@crunchify:/tmp/crunchify\# tar -zxvf crunchify.tar.gzone.txt |
| :--- |


#### 4. How to see hidden Linux files?

root@crunchify:/tmp/crunchify\# ls -ltra

#### 5. How to symlink a file in Linux?

`ln -s /path/to/file /symlink`

In below command.. when you type /tmp/java it will be redirected to /opt/java.

| root@crunchify:/tmp/crunchify\# ln -s /opt/java/ /tmp/java root@crunchify:/tmp\# pwd/tmproot@crunchify:/tmp\# ls -ltrtotal 4drwxr-xr-x 4 root root 4096 Oct  6 18:01 crunchifylrwxrwxrwx 1 root root   10 Oct  6 18:03 java -&gt; /opt/java/ |
| :--- |


How to forcefully update [Symlink](https://crunchify.com/how-to-automatically-delete-tmp-folders-in-linux-automatic-disk-log-cleanup-bash-script/)? Just use parameter `-fs`.

#### 6. How to change file permission and owner?

* `chmod` 777 &lt;filename&gt;
* `chown` root:root &lt;filename&gt;

Want to apply chmod and chown on directory? Just use parameter -R. Example: `chmod -R 777 /folder/`.

#### 7. How to remote copy file?

`scp crunchify@11.11.11.11:/tmp/crunchify/one.txt /opt/`

use parameter `-r` to copy folder.

#### 8. How to check if Java Process is running?

ps -few \| grep java

#### 9.Check since how long my VM is running?

| root@crunchify:/tmp/java\# uptime18:12:24 up 34 min,  2 users,  load average: 0.08, 0.02, 0.01 |
| :--- |


#### 10 .How to forcefully generate HeapDump of any Java Process?

$/opt/[java](https://crunchify.com/in-java-how-to-print-all-environment-properties-value-using-processbuilder/)/bin&gt; ./jmap -dump:format=b,file=/tmp/heapdump.dmp 33333 \(process ID\)

#### 11. How to check active number of connections on port 8080 every 5 seconds?

while true; do netstat -an \| grep -c $\(hostname -i\):8080; sleep 5; done;

#### 12. How to login as another user?

sudo su – crunchify

#### 13. How to Download JDK 9 from internet?

![How to Download JDK 9 from internet](https://cdn.crunchify.com/wp-content/uploads/2017/10/How-to-Download-JDK-9-from-internet.png)

Command:

| root@crunchify:/tmp/java\# curl -L -C - -b "oraclelicense=accept-securebackup-cookie" -O http://download.oracle.com/otn-pub/java/jdk/9+181/jdk-9\_linux-x64\_bin.tar.gz |
| :--- |


Want to [install Java](https://crunchify.com/where-is-java-installed-on-my-mac-osx-system/) using `system command`?

| root@crunchify:/tmp/java\# java -versionThe program 'java' can be found in the following packages: \* default-jre \* openjdk-8-jre-headless \* gcj-4.8-jre-headless \* gcj-4.9-jre-headless \* gcj-5-jre-headless \* gcj-6-jre-headless \* openjdk-9-jre-headlessTry: apt install &lt;selected package&gt; root@crunchify:/tmp/java\# apt install openjdk-9-jre-headless |
| :--- |


#### 14. How to empty a big file?

Use command: `cat /dev/null > file-name`

| root@crunchify:/opt\# ls -ltrtotal 16drwxr-xr-x 3 root root  4096 Oct  6 18:23 java-rw-r--r-- 1 root root 11729 Oct  6 18:32 one.txt root@crunchify:/opt\# cat /dev/null &gt; one.txtroot@crunchify:/opt\# ls -ltrtotal 4drwxr-xr-x 3 root root 4096 Oct  6 18:23 java-rw-r--r-- 1 root root    0 Oct  6 18:33 one.txt |
| :--- |


#### 15. How to create file without VI or VIM?

Use command `touch`.

| root@crunchify:/opt\# ls -ltrtotal 4drwxr-xr-x 3 root root 4096 Oct  6 18:23 java-rw-r--r-- 1 root root    0 Oct  6 18:33 one.txt root@crunchify:/opt\# touch two.txt root@crunchify:/opt\# ls -ltrtotal 4drwxr-xr-x 3 root root 4096 Oct  6 18:23 java-rw-r--r-- 1 root root    0 Oct  6 18:33 one.txt-rw-r--r-- 1 root root    0 Oct  6 18:36 two.txt |
| :--- |


#### 16. How to see and clear command History?

* root@crunchify:/opt\# history \(to see history\)
* root@crunchify:/opt\# history -c \(to clear history\)

#### 17. General System Information

| --------- Free and use memory -----------root@crunchify:/opt\# free -h              total        used        free      shared  buff/cache   availableMem:           989M         93M        241M        7.7M        654M        868MSwap:          511M          0B        511M --------- system info -----------root@crunchify:/opt\# uname -aLinux crunchify 4.9.36-x86\_64-linode85 \#1 SMP Thu Jul 6 15:31:23 UTC 2017 x86\_64 x86\_64 x86\_64 GNU/Linux --------- release info -----------root@crunchify:/opt\# uname -r4.9.36-x86\_64-linode85 --------- find hostname -----------root@crunchify:/opt\# hostname -fcrunchify --------- Uptime Status -----------root@crunchify:/opt\# uptime 18:41:51 up  1:04,  2 users,  load average: 0.00, 0.00, 0.00 --------- find IP -----------root@crunchify:/opt\# hostname -I74.207.254.177 2600:3c01::f03c:91ff:febd:f028 --------- Check Last Reboot time -----------root@crunchify:/opt\# last rebootreboot   system boot  4.9.36-x86\_64-li Fri Oct  6 17:37   still runningwtmp begins Fri Oct  6 17:37:40 2017 --------- find Date -----------root@crunchify:/opt\# dateFri Oct  6 18:42:09 UTC 2017 --------- Check Calendar -----------root@crunchify:/opt\# cal    October 2017      Su Mo Tu We Th Fr Sa   1  2  3  4  5  6  7   8  9 10 11 12 13 14  15 16 17 18 19 20 21  22 23 24 25 26 27 28  29 30 31               --------- check who all are online -----------root@crunchify:/opt\# w 18:42:15 up  1:04,  2 users,  load average: 0.00, 0.00, 0.00USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHATroot     ttyS0    -                17:45   55:23   0.03s  0.02s -bashroot     pts/0    216.113.160.67   17:47    7.00s  0.39s  0.00s w --------- check who you are -----------root@crunchify:/opt\# whoamiroot |
| :--- |


#### 18. Monitoring and Statistics Commands

| ------------- Display the last 20 lines of file - and follow it along -------------root@crunchify:/opt\# tail -f one.txt |
| :--- |


#### 19. Grep Command – search file

| ----------- Grep text crunchify from file one.txt -----------root@crunchify:/opt\# grep crunchify one.txt ----------- How to Find files larger than 500MB in /opt ---------find /opt -size +500M ----------- Find files in /opt/java that start with "java" -----------find /opt/java -name 'java\*' |
| :--- |


#### 20. Disk space commands

| ----------- Current directory Disk usage -----------root@crunchify:/opt\# du -sh875M . ----------- Disk usage in mounted file system -----------root@crunchify:/opt\# df -hFilesystem      Size  Used Avail Use% Mounted on/dev/root        20G  2.5G   16G  14% /devtmpfs        493M     0  493M   0% /devtmpfs           495M     0  495M   0% /dev/shmtmpfs           495M  7.7M  487M   2% /runtmpfs           5.0M     0  5.0M   0% /run/locktmpfs           495M     0  495M   0% /sys/fs/cgrouptmpfs            99M     0   99M   0% /run/user/0 ----------- Show inodes stats -----------root@crunchify:/opt\# df -iFilesystem      Inodes IUsed   IFree IUse% Mounted on/dev/root      1180608 67446 1113162    6% /devtmpfs        126148  1375  124773    2% /devtmpfs           126633     1  126632    1% /dev/shmtmpfs           126633  1191  125442    1% /runtmpfs           126633     2  126631    1% /run/locktmpfs           126633    16  126617    1% /sys/fs/cgrouptmpfs           126633     5  126628    1% /run/user/0 |
| :--- |


#### 21. Understand Linux file Permission

![Understand Linux File Permission](https://cdn.crunchify.com/wp-content/uploads/2017/10/Understand-Linux-File-Permission.png)

|         PERMISSION      EXAMPLE          U   G   O        rwx rwx rwx     chmod 777 filename        rwx rwx r-x     chmod 775 filename        rwx r-x r-x     chmod 755 filename        rw- rw- r--     chmod 664 filename        rw- r-- r--     chmod 644 filename |
| :--- |


#### 22. Handy Linux Command Cheat Sheet:

Click to expand.

[![Handy Checklist for Linux Commands](https://cdn.crunchify.com/wp-content/uploads/2017/10/Handy-Checklist-for-Linux-Commands.png)](https://cdn.crunchify.com/wp-content/uploads/2017/10/Handy-Checklist-for-Linux-Commands.png)

**Join the Discussion**

Share & leave us some comments on what you think about this topic or if you like to add something.Share: 

#### Other Popular Articles...

1. [How to change Default Java /JDK Version and ClassPath in Linux using .bash\_profile? ](https://crunchify.com/how-to-change-default-java-jdk-jvm-classpath-in-linux-using-bash_profile/)
2. [systemctl start/stop service: How to Setup Upstart Script and Respawn Process in Ubuntu, CentOS, Redhat Linux ](https://crunchify.com/systemd-upstart-respawn-process-linux-os/)
3. [Linux: How to Generate TimeoutException for a specific IP using TC qdisk and netem command? ](https://crunchify.com/linux-how-to-generate-timeoutexception-for-a-specific-ip-using-tc-command/)
4. [How to install & setup Apache Tomcat server on Linux Ubuntu host \[on Linode\] ](https://crunchify.com/how-to-install-setup-apache-tomcat-server-on-linux-ubuntu-host-on-linode/)
5. [How to Automatically Delete /tmp folders in Linux? Automatic Disk Log Cleanup Bash Script ](https://crunchify.com/how-to-automatically-delete-tmp-folders-in-linux-automatic-disk-log-cleanup-bash-script/)
6. [How to Run Windows, Linux, macOS terminal commands in Java and return complete Result](https://crunchify.com/how-to-run-windowsmac-commands-in-java-and-return-the-text-result/)

