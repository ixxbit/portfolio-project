# diskutil

[source link](https://eclecticlight.co/2017/06/15/something-odd-you-cant-fix-sierra-re-introduces-repairing-permissions/)

That should be all that you need to do, but Apple then recommends that you use an undocumented command to complete the repair. This must be performed in Terminal, where you enter:  
``diskutil resetUserPermissions / `id -u```

This apparently resets user permissions on the root volume \(/\) to the current user ID. It does not appear in `man diskutil`, nor when you just type `diskutil`, but its help info is given if you type  
`diskutil resetUserPermissions`  
You are then told  
`Usage: diskutil resetUserPermissions MountPoint|DiskIdentifier|DeviceNode UID  
Reset the permissions of a user home directory.  
Ownership of the affected disk is required.`

But that is not yet all. Apple’s support note then states that the command may fail with an error -69841, in which case you should type the following into Terminal  
`chflags -R nouchg ~`  
then try the `diskutil` command again.

This begs several questions. First, what does `diskutil resetUserPermissions` do that propagating the correct permissions does not? Why is none of this incorporated into a tool like Disk Utility? Which widely-used apps and features, including Near Lock, change permissions and cause the problem in the first place?

I’d love to hear from those who have tried this, and learn whether it did fix your problems.

