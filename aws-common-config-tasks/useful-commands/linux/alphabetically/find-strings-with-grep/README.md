---
description: How to find
---

# Find strings with grep

[https://www.tecmint.com/find-a-specific-string-or-word-in-files-and-directories/](https://www.tecmint.com/find-a-specific-string-or-word-in-files-and-directories/)

Do you want to find all files that contain a particular word or string of text on your entire Linux system or a given directory. This article will guide you on how to do that, you will learn how to recursively dig through directories to find and list all files that contain a given string of text.

A simple way to work this out is by using [grep pattern searching tool](https://www.tecmint.com/12-practical-examples-of-linux-grep-command/), is a powerful, efficient, reliable and most popular command-line utility for finding patterns and words from files or directories on Unix-like systems.

**Read Also**: [11 Advanced Linux ‘Grep’ Commands on Character Classes and Bracket Expressions](https://www.tecmint.com/linux-grep-commands-character-classes-bracket-expressions/)

The command below will list all files containing a line with the text “**check\_root**”, by recursively and aggressively searching the `~/bin` directory.

```text
$ grep -Rw ~/bin/ -e 'check_root'
```

[![Find a Word in Directory](https://www.tecmint.com/wp-content/plugins/lazy-load/images/1x1.trans.gif)](https://www.tecmint.com/wp-content/uploads/2017/12/Find-a-Word-in-Directory.png)

Find a Word in Directory

Where the `-R` option tells **grep** to read all files under each directory, recursively, following symbolic links only if they are on the command line and option **-w** instructs it to select only those lines containing matches that form whole words, and `-e` is used to specify the string \(pattern\) to be searched.

You should use the [sudo command](https://www.tecmint.com/run-shell-scripts-with-sudo-command-in-linux/) when searching certain directories or files that require root permissions \(unless you are managing your system with the root account\).

```text
 
$ sudo grep -Rw / -e 'check_root'	
```

To ignore case distinctions employ the `-i` option as shown:

```text
$ grep -Riw ~/bin/ -e 'check_root'
```

If you want to know the exact line where the string of text exist, include the `-n` option.

```text
$ grep -Rinw ~/bin/ -e 'check_root'
```

[![Find String with Line Number](https://www.tecmint.com/wp-content/plugins/lazy-load/images/1x1.trans.gif)](https://www.tecmint.com/wp-content/uploads/2017/12/Find-String-with-Line-Number.png)

Find String with Line Number

Assuming there are several types of files in a directory you wish to search in, you can also specify the type of files to be searched for instance, by their extension using the `--include` option.

This example instructs grep to only look through all `.sh` files.

```text
$ grep -Rnw --include=\*.sh ~/bin/ -e 'check_root'
```

In addition, it is possible to search for more than one pattern, using the following command.

```text
$ grep -Rinw ~/bin/ -e 'check_root' -e 'netstat'
```

[![Find Multiple Words in Files](https://www.tecmint.com/wp-content/plugins/lazy-load/images/1x1.trans.gif)](https://www.tecmint.com/wp-content/uploads/2017/12/Find-Multiple-Words-in-Files.png)

Find Multiple Words in Files

That’s It! If you know any other command-line trick to find string or word in files, do share with us or ask any questions regarding this topic, use the comment form below.

