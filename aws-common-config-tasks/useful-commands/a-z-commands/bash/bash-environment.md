# bash environment



## Customize the bash shell environments <a id="firstHeading"></a>

[Jump to navigation](https://bash.cyberciti.biz/guide/Customize_the_bash_shell_environments#mw-head)[Jump to search](https://bash.cyberciti.biz/guide/Customize_the_bash_shell_environments#p-search)

[← Bash variable existence check](https://bash.cyberciti.biz/guide/Bash_variable_existence_check) • [**Home**](https://bash.cyberciti.biz/guide/Main_Page) • [Recalling command history →](https://bash.cyberciti.biz/guide/Recalling_command_history)

* Strictly speaking there are two types of shell variables:
  1. [Local variables](https://bash.cyberciti.biz/wiki/index.php?title=Local_variables&action=edit&redlink=1) \(shell variable\) - Used by shell and or user scripts. All user created variables are **local unless exported** using the [export command](https://bash.cyberciti.biz/guide/Export_command).
  2. [Environment variables](https://bash.cyberciti.biz/wiki/index.php?title=Environment_variables&action=edit&redlink=1) - Used by shell or user but they are also passed onto other command. Environment variables are **passed to subprocesses or subshells**.

### Contents

* [1How do I configure and customize the Bash shell environment?](https://bash.cyberciti.biz/guide/Customize_the_bash_shell_environments#How_do_I_configure_and_customize_the_Bash_shell_environment.3F)
  * [1.1What should I put in shell starup files for customization?](https://bash.cyberciti.biz/guide/Customize_the_bash_shell_environments#What_should_I_put_in_shell_starup_files_for_customization.3F)
* [2How do I view local variables?](https://bash.cyberciti.biz/guide/Customize_the_bash_shell_environments#How_do_I_view_local_variables.3F)
* [3How do I export local variables?](https://bash.cyberciti.biz/guide/Customize_the_bash_shell_environments#How_do_I_export_local_variables.3F)
* [4How do I view environment variables?](https://bash.cyberciti.biz/guide/Customize_the_bash_shell_environments#How_do_I_view_environment_variables.3F)
* [5Common Environment Variables](https://bash.cyberciti.biz/guide/Customize_the_bash_shell_environments#Common_Environment_Variables)
  * [5.1How do I locate command?](https://bash.cyberciti.biz/guide/Customize_the_bash_shell_environments#How_do_I_locate_command.3F)
  * [5.2whereis command](https://bash.cyberciti.biz/guide/Customize_the_bash_shell_environments#whereis_command)
  * [5.3whatis command](https://bash.cyberciti.biz/guide/Customize_the_bash_shell_environments#whatis_command)

### How do I configure and customize the Bash shell environment?

* Your Bash shell can be configured using the following:
  1. [Variables](https://bash.cyberciti.biz/guide/Variables)
  2. [set command](https://bash.cyberciti.biz/guide/Set_command)
  3. [shopt command](https://bash.cyberciti.biz/guide/Shopt_command)
  4. [Functions](https://bash.cyberciti.biz/guide/Chapter_9:_Functions)
  5. [Alias](https://bash.cyberciti.biz/guide/Create_and_use_aliases)

#### What should I put in shell starup files for customization?

A typically Linux or UNIX user do the following:

* Setup a custom prompt.
* Setup terminal settings depending on which terminal you're using.
* Set the search path such as JAVA\_HOME, and ORACLE\_HOME.
* Set environment variables as needed by programs.
* Run commands that you want to run whenever you log in or log out.

### How do I view local variables?

Use the set built-in command to view all variables:

```text
set
```

Usually, all upper-case variables are set by bash. For example,

```text
echo $SHELL
echo $MAIL
```

### How do I export local variables?

Use the [export command](https://bash.cyberciti.biz/guide/Export_command):

```text
export EDITOR=/usr/bin/vim
# export DISPLAY environment variable and run xeyes 
export DISPLAY=localhost:11.0 xeyes
```

Be careful when changing the shell variables. For a complete list of variables set by shell, read the man page for bash by typing the following command:

```text
man bash
```

### How do I view environment variables?

Use the env command to view all environment variables:

```text
env
```

Sample outputs:

```text
ORBIT_SOCKETDIR=/tmp/orbit-vivek
SSH_AGENT_PID=4296
GPG_AGENT_INFO=/tmp/gpg-ElCDl5/S.gpg-agent:4297:1
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=186611583e30fed08439ca0047067c9d-1255929792.297209-1700262470
GTK_RC_FILES=/etc/gtk/gtkrc:/home/vivek/.gtkrc-1.2-gnome2
WINDOWID=48252673
GTK_MODULES=canberra-gtk-module
USER=vivek
SSH_AUTH_SOCK=/tmp/keyring-s4fcR1/socket.ssh
GNOME_KEYRING_SOCKET=/tmp/keyring-s4fcR1/socket
SESSION_MANAGER=local/vivek-desktop:/tmp/.ICE-unix/4109
USERNAME=vivek
DESKTOP_SESSION=gnome
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
GDM_XSERVER_LOCATION=local
PWD=/home/vivek
LANG=en_IN
GDM_LANG=en_IN
GDMSESSION=gnome
SHLVL=1
HOME=/home/vivek
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=vivek
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-16XVNAMkFB,guid=0acb6a08e3992ccc7338726c4adbf7c3
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/
WINDOWPATH=7
DISPLAY=:0.0
COLORTERM=gnome-terminal
XAUTHORITY=/home/vivek/.Xauthority
OLDPWD=/usr/share/man
_=/usr/bin/env
```

### Common Environment Variables

* HOME - Your home directory path.
* PATH - Set your executable search path.
* PWD - Your current working directory.
* See [more standard environment variables list](https://bash.cyberciti.biz/guide/Variables#Commonly_Used_Shell_Variables).

#### How do I locate command?

The which command displays the pathnames of the files which would be executed in the current environment. It does this by searching the PATH for executable files matching the names of the arguments.

```text
which command-name
```

Show fortune command path which print a random, hopefully interesting, adage on screen. Type the following command:

```text
which fortune
```

Sample output:

```text
/usr/games/fortune
```

Display your current PATH:

```text
echo $PATH
```

Sample outputs:

```text
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

Customize your PATH variable and remove /usr/games from PATH:

```text
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

Now, try searching fortune command path, enter:

```text
which fortune
```

Try executing fortune command:

```text
fortune
```

Sample outputs:

```text
-bash: fortune: command not found
```

The fortune command could not be located because '/usr/games' is not included in the PATH environment variable. You can type full command path \(/usr/games/fortune\) or simply add /usr/games to PATH variable:

```text
export PATH=$PATH:/usr/games
fortune
```

Sample outputs:

```text
Your lucky number has been disconnected.
```

#### whereis command

The [whereis command](https://bash.cyberciti.biz/wiki/index.php?title=Whereis_command&action=edit&redlink=1) is used to locate the binary, source, and manual page files for a command.

```text
whereis command-name
whereis ls
```

Sample outputs:

```text
ls: /bin/ls /usr/share/man/man1/ls.1.gz
```

#### whatis command

The [whatis command](https://bash.cyberciti.biz/wiki/index.php?title=Whatis_command&action=edit&redlink=1) is used display a short description about command. whatis command searches the manual page names and displays the manual page descriptions for a command:

```text
whatis command-name
whatis date
whatis ifconfig
whatis ping
```

Sample outputs:

```text
date (1)             - print or set the system date and time
ifconfig (8)         - configure a network interface
ping (8)             - send ICMP ECHO_REQUEST to network hosts
```

