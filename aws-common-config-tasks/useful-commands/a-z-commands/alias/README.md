# alias

## 30 Handy Bash Shell Aliases For Linux / Unix / Mac OS X

{% embed url="https://www.cyberciti.biz/tips/bash-aliases-mac-centos-linux-unix.html" %}



last updated November 16, 2018 in Categories [Linux](https://www.cyberciti.biz/tips/category/linux), [Shell scripting](https://www.cyberciti.biz/tips/category/shell-scripting), [UNIX](https://www.cyberciti.biz/tips/category/unix)[![](https://www.cyberciti.biz/media/new/category/old/terminal.png)](https://www.cyberciti.biz/tips/category/shell-scripting)

An bash alias is nothing but the shortcut to commands. The alias command allows the user to launch any command or group of commands \(including options and filenames\) by entering a single word. Use alias command to display a list of all defined aliases. You can add user-defined aliases to [~/.bashrc](https://bash.cyberciti.biz/guide/~/.bashrc) file. You can cut down typing time with these aliases, work smartly, and increase productivity at the command prompt.  
  
This post shows how to create and use aliases including 30 practical examples of bash shell aliases.  
[![30 Useful Bash Shell Aliase For Linux/Unix Users](https://www.cyberciti.biz/tips/wp-content/uploads/2012/06/Getting-Started-With-Bash-Shell-Aliases-For-Linux-Unix.jpg)](https://www.cyberciti.biz/tips/wp-content/uploads/2012/06/Getting-Started-With-Bash-Shell-Aliases-For-Linux-Unix.jpg)

Advertisements  


### More about bash shell aliases

The general syntax for the alias command for the bash shell is as follows:

#### How to list bash aliases

Type the following [alias command](https://www.cyberciti.biz/tips/bash-aliases-mac-centos-linux-unix.html):  
`alias`  
Sample outputs:

```text
alias ..='cd ..'
alias amazonbackup='s3backup'
alias apt-get='sudo apt-get'
...
```

By default alias command shows a list of aliases that are defined for the current user.

#### How to define or create a bash shell alias

To [create the alias](https://bash.cyberciti.biz/guide/Create_and_use_aliases) use the following syntax:

|  |
| :--- |


In this example, create the alias **c** for the commonly used clear command, which clears the screen, by typing the following command and then pressing the ENTER key:

|  |
| :--- |


Then, to clear the screen, instead of typing clear, you would only have to type the letter ‘c’ and press the \[ENTER\] key:

|  |
| :--- |


#### How to disable a bash alias temporarily

An [alias can be disabled temporarily](https://www.cyberciti.biz/faq/bash-shell-temporarily-disable-an-alias/) using the following syntax:

|  |
| :--- |


#### How to delete/remove a bash alias

You need to use the command [called unalias to remove aliases](https://bash.cyberciti.biz/guide/Create_and_use_aliases#How_do_I_remove_the_alias.3F). Its syntax is as follows:

|  |
| :--- |


In this example, remove the alias c which was created in an earlier example:

|  |
| :--- |


You also need to delete the alias from the [~/.bashrc file](https://bash.cyberciti.biz/guide/~/.bashrc) using a text editor \(see next section\).

#### [How to make bash shell aliases permanent](https://www.cyberciti.biz/faq/create-permanent-bash-alias-linux-unix/)

The alias c remains in effect only during the current login session. Once you logs out or reboot the system the alias c will be gone. To avoid this problem, add alias to your [~/.bashrc file](https://bash.cyberciti.biz/guide/~/.bashrc), enter:

|  |
| :--- |


The alias c for the current user can be made permanent by entering the following line:

|  |
| :--- |


Save and close the file. System-wide aliases \(i.e. aliases for all users\) can be put in the /etc/bashrc file. Please note that the alias command is built into a various shells including ksh, tcsh/csh, ash, bash and others.

#### A note about privileged access

You can add code as follows in ~/.bashrc:

|  |
| :--- |


#### A note about os specific aliases

You can add code as follows in ~/.bashrc [using the case statement](https://bash.cyberciti.biz/guide/The_case_statement):

|  |
| :--- |


### 30 bash shell aliases examples

You can define various types aliases as follows to save time and increase productivity.

#### \#1: Control ls command output

The [ls command lists directory contents](https://www.cyberciti.biz/faq/ls-command-to-examining-the-filesystem/) and you can colorize the output:

|  |
| :--- |


#### \#2: Control cd command behavior

|  |
| :--- |


#### \#3: Control grep command output

[grep command is a command-line utility for searching](https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/) plain-text files for lines matching a regular expression:

|  |
| :--- |


#### \#4: Start calculator with math support

|  |
| :--- |


#### \#4: Generate sha1 digest

|  |
| :--- |


#### \#5: Create parent directories on demand

[mkdir command](https://www.cyberciti.biz/faq/linux-make-directory-command/) is used to create a directory:

|  |
| :--- |


#### \#6: Colorize diff output

You can [compare files line by line using diff](https://www.cyberciti.biz/faq/how-do-i-compare-two-files-under-linux-or-unix/) and use a tool called colordiff to colorize diff output:

|  |
| :--- |


#### \#7: Make mount command output pretty and human readable format

|  |
| :--- |


#### \#8: Command short cuts to save time

|  |
| :--- |


#### \#9: Create a new set of commands

|  |
| :--- |


#### \#10: Set vim as default

|  |
| :--- |


#### \#11: Control output of networking tool called ping

|  |
| :--- |


#### \#12: Show open ports

Use [netstat command](https://www.cyberciti.biz/faq/how-do-i-find-out-what-ports-are-listeningopen-on-my-linuxfreebsd-server/) to quickly list all TCP/UDP port on the server:

|  |
| :--- |


#### \#13: Wakeup sleeping servers

[Wake-on-LAN \(WOL\) is an Ethernet networking](https://www.cyberciti.biz/tips/linux-send-wake-on-lan-wol-magic-packets.html) standard that allows a server to be turned on by a network message. You can [quickly wakeup nas devices](https://bash.cyberciti.biz/misc-shell/simple-shell-script-to-wake-up-nas-devices-computers/) and server using the following aliases:

|  |
| :--- |


#### \#14: Control firewall \(iptables\) output

[Netfilter is a host-based firewall](https://www.cyberciti.biz/faq/rhel-fedorta-linux-iptables-firewall-configuration-tutorial/) for Linux operating systems. It is included as part of the Linux distribution and it is activated by default. This [post list most common iptables solutions](https://www.cyberciti.biz/tips/linux-iptables-examples.html) required by a new Linux user to secure his or her Linux operating system from intruders.

|  |
| :--- |


#### \#15: Debug web server / cdn problems with curl

|  |
| :--- |


#### \#16: Add safety nets

|  |
| :--- |


#### \#17: Update Debian Linux server

[apt-get command](https://www.cyberciti.biz/tips/linux-debian-package-management-cheat-sheet.html) is used for installing packages over the internet \(ftp or http\). You can also upgrade all packages in a single operations:

|  |
| :--- |


#### \#18: Update RHEL / CentOS / Fedora Linux server

[yum command](https://www.cyberciti.biz/faq/rhel-centos-fedora-linux-yum-command-howto/) is a package management tool for RHEL / CentOS / Fedora Linux and friends:

|  |
| :--- |


#### \#19: Tune sudo and su

|  |
| :--- |


#### \#20: Pass halt/reboot via sudo

[shutdown command](https://www.cyberciti.biz/faq/howto-shutdown-linux/) bring the Linux / Unix system down:

|  |
| :--- |


#### \#21: Control web servers

|  |
| :--- |


#### \#22: Alias into our backup stuff

|  |
| :--- |


#### \#23: Desktop specific – play avi/mp3 files on demand

|  |
| :--- |


#### \#24: Set default interfaces for sys admin related commands

[vnstat is console-based network](https://www.cyberciti.biz/tips/keeping-a-log-of-daily-network-traffic-for-adsl-or-dedicated-remote-linux-box.html) traffic monitor. [dnstop is console tool](https://www.cyberciti.biz/faq/dnstop-monitor-bind-dns-server-dns-network-traffic-from-a-shell-prompt/) to analyze DNS traffic. [tcptrack and iftop commands displays](https://www.cyberciti.biz/faq/check-network-connection-linux/) information about TCP/UDP connections it sees on a network interface and display bandwidth usage on an interface by host respectively.

|  |
| :--- |


#### \#25: Get system memory, cpu usage, and gpu memory info quickly

|  |
| :--- |


#### \#26: Control Home Router

The curl command can be used to [reboot Linksys routers](https://www.cyberciti.biz/faq/reboot-linksys-wag160n-wag54-wag320-wag120n-router-gateway/).

|  |
| :--- |


#### \#27 Resume wget by default

The [GNU Wget is a free utility for non-interactive download](https://www.cyberciti.biz/tips/wget-resume-broken-download.html) of files from the Web. It supports HTTP, HTTPS, and FTP protocols, and it can resume downloads too:

|  |
| :--- |


#### \#28 Use different browser for testing website

|  |
| :--- |


#### \#29: A note about ssh alias

Do not create ssh alias, instead use ~/.ssh/config OpenSSH SSH client configuration files. It offers more option. An example:

|  |
| :--- |


You can now connect to peer1 using the following syntax:  
`$ ssh server10`

#### \#30: It’s your turn to share…

|  |
| :--- |


### Conclusion

This post summarizes several types of uses for \*nix bash aliases:

1. Setting default options for a command \(e.g. set eth0 as default option for ethtool command via alias ethtool='ethtool eth0' \).
2. Correcting typos \(cd.. will act as cd .. via alias cd..='cd ..'\).
3. Reducing the amount of typing.
4. Setting the default path of a command that exists in several versions on a system \(e.g. GNU/grep is located at /usr/local/bin/grep and Unix grep is located at /bin/grep. To use GNU grep use alias grep='/usr/local/bin/grep' \).
5. Adding the safety nets to Unix by making commands interactive by setting default options. \(e.g. rm, mv, and other commands\).
6. Compatibility by creating commands for older operating systems such as MS-DOS or other Unix like operating systems \(e.g. alias del=rm \).

I’ve shared my aliases that I used over the years to reduce the need for repetitive command line typing. If you know and use any other bash/ksh/csh aliases that can reduce typing, share below in the [comments](https://www.nixcraft.com/t/30-handy-bash-shell-aliases-for-linux-unix-mac-os-x/1458).

