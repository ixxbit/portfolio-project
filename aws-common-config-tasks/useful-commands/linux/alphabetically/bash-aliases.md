---
description: How to Create Bash Aliases
---

# Bash Aliases

![](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVR42mP8+PXHfwAJnAPfCuZXlQAAAABJRU5ErkJggg==)

Do you often find yourself typing a long command on the command line or searching the bash history for a previously typed command? If your answer to any of those questions is yes, then you will find bash aliases handy. Bash aliases allow you to set a memorable shortcut command for a longer command.

Bash aliases are essentially shortcuts that can save you from having to remember long commands and eliminate a great deal of typing when you are working on the command line. For example, you could set the alias `tgz` to be a shortcut for the [`tar -xvfz` command](https://linuxize.com/post/how-to-create-and-extract-archives-using-the-tar-command-in-linux/).

This article explains how to create bash aliases so you can be more productive on the command line.

## Creating Bash Aliases [\#](https://linuxize.com/post/how-to-create-bash-aliases/#creating-bash-aliases) <a id="creating-bash-aliases"></a>

Creating aliases in bash is very straight forward. The syntax is as follows:

```text
alias alias_name="command_to_run"
```

An alias declaration starts with the `alias` keyword followed by the alias name, an equal sign and the command you want to run when you type the alias. The command needs to be enclosed in quotes and with no spacing around the equal sign. Each alias needs to be declared on a new line.

The `ls` command is probably one of the most used commands on the Linux command line. I usually use this command with the `-la` switch to list out all files and directories, including the hidden ones in long list format.

Let’s create a simple bash alias named `ll` which will be a shortcut for the [`ls -la` command](https://linuxize.com/post/how-to-list-files-in-linux-using-the-ls-command/). To do so type open a terminal window and type:

```text
alias ll="ls -la"
```

Now, if you type `ll` in your terminal, you’ll get the same output as you would by typing `ls -la`.

The `ll` alias will be available only in the current shell session. If you exit the session or open a new session from another terminal, the alias will not be available.

To make the alias persistent you need to declare it in the `~/.bash_profile` or `~/.bashrc` file.

Open the `~/.bashrc` in your [text editor](https://linuxize.com/post/how-to-use-nano-text-editor/):

```text
nano ~/.bashrc
```

and add your aliases:

~/.bashrc

```text
# Aliases
# alias alias_name="command_to_run"

# Long format list
alias ll="ls -la"

# Print my public IP
alias myip='curl ipinfo.io/ip'
```

The aliases should be named in a way that is easy to remember. It is also recommended to add a comment for future reference.

Once done, save and close the file. Make the aliases available in your current session by typing:

```text
source ~/.bash_profile
```

As you can see, creating simple bash aliases is quick and very easy.

If you want to make your `.bashrc` more modular you can store your aliases in a separate file. Some distributions like Ubuntu and Debian include a `.bash_aliases` file, which is sourced from the `~/.bashrc`.

## Creating Bash Aliases with Arguments \(Bash Functions\) [\#](https://linuxize.com/post/how-to-create-bash-aliases/#creating-bash-aliases-with-arguments-bash-functions) <a id="creating-bash-aliases-with-arguments-bash-functions"></a>

Sometimes you may need to create an alias that accepts one or more arguments. That’s where bash functions come in handy.

The syntax for creating a [bash function](https://linuxize.com/post/bash-functions/) is very easy. They can be declared in two different formats:

```text
function_name () {
  [commands]
}
```

or

```text
function function_name {
  [commands]
}
```

To pass any number of arguments to the bash function simply, put them right after the function’s name, separated by a space. The passed parameters are `$1`, `$2`, `$3`, etc., corresponding to the position of the parameter after the function’s name. The `$0` variable is reserved for the function name.

Let’s create a simple bash function which will [create a directory](https://linuxize.com/post/how-to-create-directories-in-linux-with-the-mkdir-command/) and then navigate into it:

~/.bashrc

```text
mkcd ()
{
  mkdir -p -- "$1" && cd -P -- "$1"
}
```

Same as with aliases, add the function to your `~/.bashrc` file and run `source ~/.bash_profile` to reload the file.

Now instead of using `mkdir` to create a new directory and then `cd` to [move into that directory](https://linuxize.com/post/linux-cd-command/), you can simply type:

```text
mkcd new_directory
```

If you wonder what are `--` and `&&` here is a short explanation.

* `--` - makes sure you’re not accidentally passing an extra argument to the command. For example, if you try to create a directory that starts with `-` \(dash\) without using `--` the directory name will be interpreted as a command argument.
* `&&` - ensures that the second command runs only if the first command is successful.

## Conclusion [\#](https://linuxize.com/post/how-to-create-bash-aliases/#conclusion) <a id="conclusion"></a>

By now you should have a good understanding of how to create bash aliases and functions that will make your life on the command line easier and more productive.

If you have any questions or feedback, feel free to leave a comment.

