# links

How do I create a symbolic links under Linux or Unix like operating systems using command line options?  
  
You need to use the ln command. It is a standard Unix / Linux / BSD command to create links to files. There are two types of links under UNIX, hard and soft link:

Advertisements  


### [Hard link vs. Soft link](https://www.cyberciti.biz/tips/understanding-unixlinux-symbolic-soft-and-hard-links.html) in Linux or UNIX

\[a\] Hard links cannot links directories \( cannot link /tmp with /home/you/tmp\)

\[b\] Hard links cannot cross file system boundaries \( cannot link /tmp mounted on/tmp to 2nd hard disk mounted on /harddisk2\)

\[c\] Symbolic links refer to a **symbolic path indicating the abstract location** of another file

\[d\] Hard links, refer to the specific location of **physical data**.

### UNIX create a symbolic link command

To **create a symbolic link**, enter:  
`$ ln -s {/path/to/file-name} {link-name}  
$ ln -s /shared/sales/data/file.txt sales.data.txt  
$ vi sales.data.txt  
$ ls -l sales.data.txt`

#### How do I delete a symbolic link?

To delete a link, enter:  
`$ rm {link-name}  
$ rm sales.data.txt  
$ ls -l  
$ ls -l /shared/sales/data/file.txt`  
If you delete the soft link itself \(sales.data.txt\) , the data file would still be there \( /shared/sales/data/file.txt \). However, if you delete /shared/sales/data/file.txt, sales.data.txt becomes a broken link and data is lost.

### UNIX create a hardlink command

To **create hard link**, enter \(without the -s option\):  
`$ ln {file.txt} {hard-link}  
$ ln /tmp/file link-here`

#### How do I delete a hard link?

You can delete hard link with the rm command itself:  
`$ rm {hard-link}  
$ rm link-here`  
If you delete a hard link, your data would be there. If you delete /tmp/file your data still be accessible via link-here hard link file.

