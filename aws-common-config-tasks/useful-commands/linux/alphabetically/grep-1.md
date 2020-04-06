# Grep

[https://www.howtoforge.com/tutorial/linux-grep-command/](https://www.howtoforge.com/tutorial/linux-grep-command/)

This website uses cookies to ensure you get the best experience on our website, analyze site traffic and show you relevant ads. [More inf](https://www.howtoforge.com/community/help/cookies)

[Home](https://www.howtoforge.com/)[How to use grep to search for strings in files on the shell](https://www.howtoforge.com/tutorial/linux-grep-command/)[Scan your Web-Server for Malware with ISPProtect now. Get Free Trial.](https://ispprotect.com/?pk_campaign=htftxt)

#### On this page

1. [1 The GREP command- an overview](https://www.howtoforge.com/tutorial/linux-grep-command/#-the-grep-command-an-overview)
2. [2 The basic grep command syntax](https://www.howtoforge.com/tutorial/linux-grep-command/#-the-basic-grep-command-syntax)
3. [3 How to use the grep command for searching in a file](https://www.howtoforge.com/tutorial/linux-grep-command/#-how-to-use-the-grep-command-for-searching-in-a-file)
4. [4 Recursive use of grep](https://www.howtoforge.com/tutorial/linux-grep-command/#-recursive-use-of-grep)
5. [5 Using grep to search only for words](https://www.howtoforge.com/tutorial/linux-grep-command/#-using-grep-to-search-only-for-words)
6. [6 Using grep to search two different words](https://www.howtoforge.com/tutorial/linux-grep-command/#-using-grep-to-search-two-different-words)
7. [7 Count lines for matched words](https://www.howtoforge.com/tutorial/linux-grep-command/#-count-lines-for-matched-words)
8. [8 Grep invert match](https://www.howtoforge.com/tutorial/linux-grep-command/#-grep-invert-match)
9. [9 How to list only the names of matching files](https://www.howtoforge.com/tutorial/linux-grep-command/#-how-to-list-only-the-names-of-matching-files)
10. [10 How to make grep command handle multiple search patterns](https://www.howtoforge.com/tutorial/linux-grep-command/#-how-to-make-grep-command-handle-multiple-search-patterns)
11. [11 How to limit grep output to a particular number of lines](https://www.howtoforge.com/tutorial/linux-grep-command/#-how-to-limit-grep-output-to-a-particular-number-of-lines)
12. [12 How to make grep obtain patterns from file](https://www.howtoforge.com/tutorial/linux-grep-command/#-how-to-make-grep-obtain-patterns-from-file)
13. [13 How to make grep display only those lines that completely match the search pattern](https://www.howtoforge.com/tutorial/linux-grep-command/#-how-to-make-grep-display-only-those-lines-that-completely-match-the-search-pattern)
14. [14 How to force grep to not display anything in the output](https://www.howtoforge.com/tutorial/linux-grep-command/#-how-to-forcenbspgrep-to-not-display-anything-in-the-output)
15. [15 How to make grep display name of files that do not contain search pattern](https://www.howtoforge.com/tutorial/linux-grep-command/#-how-to-make-grep-display-name-of-files-that-do-not-contain-search-pattern)
16. [16 How to suppress error messages produced by grep](https://www.howtoforge.com/tutorial/linux-grep-command/#-how-to-suppress-error-messages-produced-by-grep)
17. [17 How to make grep recursively search directories](https://www.howtoforge.com/tutorial/linux-grep-command/#-how-to-make-grep-recursively-search-directories)
18. [18 How to make grep terminate file names with NULL character](https://www.howtoforge.com/tutorial/linux-grep-command/#-how-to-make-grep-terminate-file-names-with-null-character)
19. [19 More GREP command examples](https://www.howtoforge.com/tutorial/linux-grep-command/#-more-grep-command-examples)

### 1 The GREP command- an overview <a id="-the-grep-command-an-overview"></a>

The grep command, which means **global regular expression print**, remains amongst the most versatile commands in a Linux terminal environment. It happens to be an immensely powerful program that lends users the ability to sort input based on complex rules, thus rendering it a fairly popular link across numerous command chains. The grep command is primarily used to search text or search any given file for lines containing a match to the supplied words/strings. By default, grep displays the matching lines, and it may be used to search for lines of text matching one/many regular expressions in a fuss-free, and it outputs only the matching lines.

### 2 The basic grep command syntax <a id="-the-basic-grep-command-syntax"></a>

The basic grep command syntax is as follows:

```text
grep 'word' filename
grep 'word' file1 file2 file3
grep 'string1 string2'  filename
cat otherfile | grep 'something'
command | grep 'something'
command option1 | grep 'data'
grep --color 'data' fileName
```

### 3 How to use the grep command for searching in a file <a id="-how-to-use-the-grep-command-for-searching-in-a-file"></a>

In the first example, I will search for the user "tom" in the Linux passwd file. To search the /etc/passwd file for the user "tom", you need to enter the following command:

```text
grep tom /etc/passwd
```

Given below is the sample Output:

```text
tom:x:1000:1000:tom,,,:/home/tom:/bin/bash
```

You have the option to instruct grep to ignore word case, i.e., match abc, Abc, ABC and all possible combinations with the -i option as shown below:

```text
grep -i "tom" /etc/passwd
```

### 4 Recursive use of grep <a id="-recursive-use-of-grep"></a>

If you have a bunch of text files in a directory hierarchy, e.g, the Apache configuration files in /etc/apache2/ and you want to find the file where a specific text is defined, then use the -r option of the grep command to do a recursive search. This will perform a recursive search operation trough files for the string "197.167.2.9" \(as shown below\) in the directory /etc/apache2/ and all its sub-directories:

```text
grep -r "mydomain.com" /etc/apache2/
```

Alternatively, the following command may be used:

```text
grep -R "mydomain.com" /etc/apache2/
```

Given below are the Sample outputs for a similar search on an Nginx server:

```text
grep -r "mydomain.com" /etc/nginx/
/etc/nginx/sites-available/mydomain.com.vhost:        if ($http_host != "www.mydomain.com") {
```

Here, you would see the result for mydomain.com on a distinct line preceded by the name of the file \(for instance /etc/nginx/sites-available/mydomain.com.vhost\) in which it was found. The inclusion of the file names in the output data may be easily suppressed by using the -h option \(as explained below\): grep -h -R "mydomain.com" /etc/nginx/. Given below is the sample Output:

```text
grep -r "mydomain.com" /etc/nginx/
if ($http_host != "www.mydomain.com") {
```

### 5 Using grep to search only for words <a id="-using-grep-to-search-only-for-words"></a>

When you are searching for abc, grep will match all sorts of things, viz., kbcabc, abc123, aarfbc35 and lots more combinations without obeying word boundaries. You can compel the grep command to select only those lines that contain matches to form whole words \(those that match only abc word\), as shown below:

```text
grep -w "abc" file
```

### 6 Using grep to search two different words <a id="-using-grep-to-search-two-different-words"></a>

To search for two different words, you must use the egrep command as shown below:

```text
egrep -w 'word1|word2' /path/to/file
```

### 7 Count lines for matched words <a id="-count-lines-for-matched-words"></a>

The grep command has the ability to report the number of times a particular pattern has been matched for each file using the -c \(count\) option \(as shown below\):

```text
grep -c 'word' /path/to/file
```

In addition, users may use the '-n' option preceding each output line with the number of the line in the text file from which it was obtained \(as shown below\):

```text
grep -n 'root' /etc/passwd
```

Given below are the Sample outputs:

```text
1:root:x:0:0:root:/root:/bin/bash
```

### 8 Grep invert match <a id="-grep-invert-match"></a>

Users may make use of the -v option to print inverts the match, which means it would match only those lines that do not contain the given word. For instance, print all lines that do not contain the word par by using the following command:

```text
grep -v par /path/to/file
```

### 9 How to list only the names of matching files <a id="-how-to-list-only-the-names-of-matching-files"></a>

You must use the -l option to list file names whose contents mention a particular word, for instance, the word 'primary', using the following command:

```text
grep -l 'primary' *.c
```

Lastly, you have the option to compel grep to display output in specific colors by using the following command:

```text
grep --color root /etc/passwd
```

Given below are Sample Outputs:

[![List only names of matching files with grep](https://www.howtoforge.com/images/grep_command_overview/1.png)](https://www.howtoforge.com/images/grep_command_overview/big/1.png)

### 10 How to make grep command handle multiple search patterns <a id="-how-to-make-grep-command-handle-multiple-search-patterns"></a>

There could be situations wherein you might want to search multiple patterns in a given file \(or set of files\). In such scenarios, you should use the '_-e'_ command-line option that grep provides.

For example, suppose you want to search for words "how", "to", and "forge" in all the text files present in your current working directory, then here's how you can do this:

```text
grep -e how -e to -e forge *.txt
```

Here's the command in action:

[![Multiple search patterns in Grep](https://www.howtoforge.com/images/grep_command_overview/grep-e-option.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-e-option.png)

The '_-e'_ command-line option also helps in scenarios wherein the pattern begins with a hyphen \(-\). For example, if you want to search for, say, "-how", then the following command won't be helpful:

```text
grep -how *.txt
```

It's when you use the -e command-line option, the command understands what exactly you are trying to search in this case:

```text
grep -e -how *.txt
```

Here are both commands in action:

[![Grep -e switch](https://www.howtoforge.com/images/grep_command_overview/grep-e-hyphen.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-e-hyphen.png)

### 11 How to limit grep output to a particular number of lines <a id="-how-to-limit-grep-output-to-a-particular-number-of-lines"></a>

In case you want to limit the grep output to a particular number of lines, you can do that using the '_-m'_ command-line option. For example, suppose you want to search for the word "how" in testfile1.txt which contains the following lines:

[![Limit Grep output](https://www.howtoforge.com/images/grep_command_overview/grep-testfile.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-testfile.png)

But the requirement is for grep to stop searching after 3 lines containing the searched pattern have been found. So, to do this, you can run the following command:

```text
grep "how" -m3 testfile1.txt
```

Here's the command in action:

[![Grep -m switch](https://www.howtoforge.com/images/grep_command_overview/grep-max-matches.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-max-matches.png)

Moving on, here is what the command's man page says:

```text
If the input is standard input from a regular file, and NUM matching lines are output, grep ensuresthat the standard input is positioned to just after the last matching line before exiting, regardless of the presence of trailing context lines. This enables a calling process to resume a search.
```

So for example, if you have a bash script that has a loop, and you want to fetch one match per loop iteration, then using 'grep -m1' will do the needful.

### 12 How to make grep obtain patterns from file <a id="-how-to-make-grep-obtain-patterns-from-file"></a>

If you want, you can also make the grep command obtain patterns from a file. The tool's -f command-line option lets you do this. 

For example, suppose you want to search all the .txt files in the current directory for words "how" and "to", but want to supply these input strings through a file named, say, "input," then here's how you can do this:

```text
grep -f input *.txt
```

Here's the command in action:

[![Grep optain patterns for file](https://www.howtoforge.com/images/grep_command_overview/grep-pattern-from-file.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-pattern-from-file.png)

### 13 How to make grep display only those lines that completely match the search pattern <a id="-how-to-make-grep-display-only-those-lines-that-completely-match-the-search-pattern"></a>

Up until now, we have seen that by default grep matches and displays complete lines that contain search patterns. But if the requirement is to make grep only display those lines that completely match the searched pattern, then this can be done using the '-x' command-line option.

For example, suppose testfile1.txt file contains the following lines:

[![Display exact matches only](https://www.howtoforge.com/images/grep_command_overview/grep-complete-match-testfile.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-complete-match-testfile.png)

And the pattern you want to search is "how are you?". So to make sure that grep only displays lines that completely match this pattern, use it in the following way:

```text
grep -x "how are you?" *.txt
```

Here's the command in action:

[![Grep -x switch in action](https://www.howtoforge.com/images/grep_command_overview/grep-match-complete-lines.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-match-complete-lines.png)

### 14 How to force grep to not display anything in the output <a id="-how-to-forcenbspgrep-to-not-display-anything-in-the-output"></a>

There might be situations wherein you don't need the grep command to produce anything in the output. Instead, you just want to know whether or not a match was found based on the command's exit status. This can be achieved using the -q command-line option.

While the -q option mutes the output, the tool's exit status can be confirmed by the 'echo $?' command. In the case of grep, the command exits with '0' status when it's successful \(meaning, a match was found\), while it exits with status '1' when no match was found.

The following screenshot shows both the successful and unsuccessful scenarios:

[![Grep do not display output](https://www.howtoforge.com/images/grep_command_overview/grep-exit-status.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-exit-status.png)

### 15 How to make grep display name of files that do not contain search pattern <a id="-how-to-make-grep-display-name-of-files-that-do-not-contain-search-pattern"></a>

By default, the grep command displays the name of files containing the search pattern \(as well as matched lines\). This is quite logical, as that's what expected of this tool. However, there might be cases wherein the requirement could be to get names of those files that do not contain the searched pattern.

This is also possible with grep - the _-L_ options lets you do this. So, for example, to find all those text files in the current directory that does not contain the word "how", you can run the following command:

```text
grep -L "how" *.txt
```

Here's the command in action:

[![Grep inverse match](https://www.howtoforge.com/images/grep_command_overview/grep-invert-search.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-invert-search.png)

### 16 How to suppress error messages produced by grep <a id="-how-to-suppress-error-messages-produced-by-grep"></a>

If you want, you can also force grep to mute any error messages it displays in the output. This can be done using the -s command line option. For example, consider the following scenario in which grep produces error/warning related to the directory it encounters:

[![Suppress errors in grep](https://www.howtoforge.com/images/grep_command_overview/grep-directory-error.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-directory-error.png)

So in these kind of scenarios, the -s command line option helps. See below.

[![The grep -s switch](https://www.howtoforge.com/images/grep_command_overview/grep-s-option.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-s-option.png)

So you can see that the error/warning got muted.

### 17 How to make grep recursively search directories <a id="-how-to-make-grep-recursively-search-directories"></a>

As clear from the example used in the previous point, the grep command doesn't do a recursive search by default. To make sure your grep search is recursive, use the -d command-line option and pass the value 'recurse' to it.

```text
grep -d recurse "how" *
```

_**Note1**: The directory related error/warning message we discussed in the previous point can also be muted using the -d option - all you have to do is to pass the value 'skip' to it._

_**Note2**: Use '--exclude-dir=\[DIR\]' option to exclude directories matching the pattern DIR from recursive searches._

### 18 How to make grep terminate file names with NULL character <a id="-how-to-make-grep-terminate-file-names-with-null-character"></a>

As we have already discussed, the -l command-line option of grep is used when you only want the tool to display filenames in the output. For example:

[![Grep null file termination](https://www.howtoforge.com/images/grep_command_overview/grep-l-option.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-l-option.png)

Now, what you should know here is that each name in the above output is separated/terminated by a newline character. Here's how you can verify that:

Redirect the output to a file, and then print the file contents:

[![Grep -l switch](https://www.howtoforge.com/images/grep_command_overview/grep-verify-newline.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-verify-newline.png)

So the output of the cat command confirms the presence of a newline character between the file names.

But as you might already know, the newline character can be part of a file name as well. So when dealing with cases where-in filenames contain newline and they are separated/terminated by newline as well, it becomes difficult to work on the grep output \(especially when accessing the output through a script\).

It would be good if the separating/terminating character is not newline. Well, you'll be glad to know that grep provides a command-line option -Z that makes sure filenames are followed by a NULL character and not a newline.

So, in our case, the command becomes:

```text
grep -lZ "how" *.txt
```

Here's how we confirmed the presence of NULL character:

[![Check for NULL character](https://www.howtoforge.com/images/grep_command_overview/grep-verify-null.png)](https://www.howtoforge.com/images/grep_command_overview/big/grep-verify-null.png)

Following is a related command-line option that you should know:

```text
 -z, --null-data
Treat the input as a set of lines, each terminated by a zero byte (the ASCII NUL character) insteadof a newline. Like the -Z or --null option, this option can be used with commands like sort -z to process arbitrary file names.
```

### 19 More GREP command examples <a id="-more-grep-command-examples"></a>

In our second GREP command tutorial, you can find even more examples of how to use this Linux command.

* [How to perform pattern search in files using Grep](https://www.howtoforge.com/tutorial/how-to-perform-pattern-search-in-files-using-grep/)

**About Srijan Kishore**

Over 8 years of experience as a Linux System Engineer. Srijan is an RHCE \(Red Hat Certified Engineer\) with in-depth knowledge in RHEL and CentOS, he also worked a lot with Debian and Ubuntu based systems, VM management and installing and maintaining hosting servers.

