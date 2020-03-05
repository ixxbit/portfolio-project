---
description: chown command changes the user and/or group ownership of for given file
---

# chown

#### Examples

First, list permissions for demo.txt, enter:  
`# ls -l demo.txt`  
Sample outputs:

```text
-rw-r--r-- 1 root root 0 Aug 31 05:48 demo.txt
```

In this example change file ownership to vivek user and list the permissions, run:  
`# chown vivek demo.txt  
# ls -l demo.txt`  
Sample outputs:

```text
-rw-r--r-- 1 vivek root 0 Aug 31 05:48 demo.txt
```

In this next example, the owner is set to vivek followed by a colon and a group onwership is also set to vivek group, run:  
`# chown vivek:vivek demo.txt  
# ls -l demo.txt`  
Sample outputs:

```text
-rw-r--r-- 1 vivek vivek 0 Aug 31 05:48 demo.txt
```

In this example, change only the group of file. To do so, the colon and following GROUP-name ftp are given, but the owner is omitted, only the group of the files is changed:  
`# chown :ftp demo.txt  
# ls -l demo.txt`  
Sample outputs:

```text
-rw-r--r-- 1 vivek ftp 0 Aug 31 05:48 demo.txt
```

Please note that if only a colon is given, or if NEW-OWNER is empty, neither the owner nor the group is changed:  
`# chown : demo.txt`  
In this example, change the owner of /foo to “root”, execute:  
`# chown root /foo`  
Likewise, but also change its group to “httpd”, enter:  
`# chown root:httpd /foo`  
Change the owner of /foo and subfiles to “root”, run:  
`# chown -R root /u`  
Where,

* -R – Recursively change ownership of directories and their contents.

