---
description: in Linux
---

# Adding a Directory to PATH

![](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVR42mP8+PXHfwAJnAPfCuZXlQAAAABJRU5ErkJggg==)

When you type a command on the command line, you’re basically telling the shell to run an executable file with the given name. In Linux these executable programs like [`ls`](https://linuxize.com/post/how-to-list-files-in-linux-using-the-ls-command/), [`find`](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/), [`file`](https://linuxize.com/post/linux-file-command/) and others, usually live inside several different directories on your system. Any file with executable permissions stored in these directories can be run from any location. The most common directories that hold executable programs are `/bin`, `/sbin`, `/usr/sbin`, `/usr/local/bin` and `/usr/local/sbin`.

But how does the shell knows, what directories to search for executable programs or does the shell search through the whole filesystem?

The answer is simple. When you type a command, the shell searches through all directories specified in the user `$PATH` variable for an executable file of that name.

This article shows how to add directories to your `$PATH` in Linux systems.

## What is `$PATH` in Linux [\#](https://linuxize.com/post/how-to-add-directory-to-path-in-linux/#what-is-path-in-linux) <a id="what-is-path-in-linux"></a>

The `$PATH` [environmental variable](https://linuxize.com/post/how-to-set-and-list-environment-variables-in-linux/) is a colon-delimited list of directories that tells the shell which directories to search for executable files.

To check what directories are in your `$PATH`, you can use either the `printenv` or [`echo`](https://linuxize.com/post/echo-command-in-linux-with-examples/) command:

```text
echo $PATH
```

The output will look something like this:

```text
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```

If you have two executable files sharing the same name located in two different directories the shell will run the file that lives in the directory which comes first in the `$PATH`.

## Adding a Directory to your `$PATH` [\#](https://linuxize.com/post/how-to-add-directory-to-path-in-linux/#adding-a-directory-to-your-path) <a id="adding-a-directory-to-your-path"></a>

There are situations where you may want to add other directories the `$PATH` variable. For example, some programs may be installed in different locations or you may want to have a dedicated directory for your personal scrips, but be able to run them without specifying the absolute path to the executable files. To do this you simply need to add the directory to your `$PATH`.

Let’s say you have a directory called `bin` located in your Home directory in which you keep your shell scripts. To add the directory to your `$PATH` type in:

```text
export PATH="$HOME/bin:$PATH"
```

The `export` command will export the modified variable to the shell child process environments.

You can now run your scripts simply by typing the executable script name without needing to specify the executable full path.

However, this change is only temporary and valid only in the current shell session.

To make the change permanent, you need to define the `$PATH` variable in the shell configuration files. In most Linux distributions when you start a new session, environment variables are read from the following files:

* Global shell specific configuration files such as `/etc/environment` and `/etc/profile`. Use this file if you want the new directory to be added to all system users `$PATH`.
* Per-user shell specific configuration files. For example, if you are using Bash, you can set the `$PATH` variable in the `~/.bashrc` file and if you are using Zsh the file name is `~/.zshrc`.

In this example, we’ll set the variable in the `~/.bashrc` file. Open the file with your [text editor](https://linuxize.com/post/how-to-use-nano-text-editor/) and add the following line at the end of it:

```text
nano ~/.bashrc
```

~/.bashrc

```text
export PATH="$HOME/bin:$PATH"
```

Save the file and load the new `$PATH` into the current shell session using the [`source`](https://linuxize.com/post/bash-source-command/) command:

```text
source ~/.bashrc
```

To confirm that the directory was successfully added, print the value of your `$PATH` by typing:

```text
echo $PATH
```

## Conclusion [\#](https://linuxize.com/post/how-to-add-directory-to-path-in-linux/#conclusion) <a id="conclusion"></a>

Adding new directories to your user or global `$PATH` variable is pretty simple. This allows you execute commands and scripts stored on nonstandard locations without needing to type the full path to the executable.

The same instructions apply for any Linux distribution, including Ubuntu, CentOS, RHEL, Debian and Linux Mint.

Feel free to leave a comment if you have any questions.

