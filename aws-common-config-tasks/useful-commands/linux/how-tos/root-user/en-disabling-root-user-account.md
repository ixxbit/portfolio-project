---
description: in Ubuntu
---

# En/Disabling Root User Account

![](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVR42mP8+PXHfwAJnAPfCuZXlQAAAABJRU5ErkJggg==)

As a new Ubuntu user, you may wonder how to log in to your Ubuntu system as a root user or what is the default root password. In Ubuntu Linux, the root user account is disabled by default for security reasons.

This tutorial explains how to enable and disable the root user account in Ubuntu Linux.

## Sudo Users [\#](https://linuxize.com/post/how-to-enable-and-disable-root-user-account-in-ubuntu/#sudo-users) <a id="sudo-users"></a>

Ubuntu users are encouraged to perform system administrative tasks by granting administrative privileges to a regular user using a tool named sudo. Sudo allows authorized users to run programs as another user, usually the root user.

By default on Ubuntu systems, members of the group sudo are granted with sudo access. The initial user created by the Ubuntu installer is already a member of the sudo group. Chances are that the user you are logged in as is already granted with administrative privileges.

If you want to grant sudo access to another user, simply add the user to the sudo group:

```text
usermod -aG sudo username
```

To temporarily elevate root user privileges, run the command prefixed with sudo:

```text
sudo some-command
```

The first time you use sudo in a session, you will be prompted to enter the user password.

If you want to run a command with sudo privileges without entering the password, you’ll need to edit the [`sudoers`](https://linuxize.com/post/how-to-use-nano-text-editor/) file. To do so type `visudo`:

```text
sudo visudo
```

This will open the `/etc/sudoers` file with your favorite [command line text editor](https://linuxize.com/post/how-to-add-user-to-sudoers-in-ubuntu/). Add the following line by replacing `username` with your username:

/etc/sudoers

```text
username ALL=(ALL) NOPASSWD: ALL
```

## Enable Root User Account in Ubuntu [\#](https://linuxize.com/post/how-to-enable-and-disable-root-user-account-in-ubuntu/#enable-root-user-account-in-ubuntu) <a id="enable-root-user-account-in-ubuntu"></a>

If for some reason, you need to enable the root account, you just need to set a [password for the root user](https://linuxize.com/post/how-to-change-root-password-in-ubuntu/). In Ubuntu and other Linux distributions, you can set or change the password of a user account with the [`passwd`](https://linuxize.com/post/how-to-change-user-password-in-ubuntu/) command.

As a regular user in Ubuntu, you can only change your own password. The user you are logged in as must have [sudo privileges](https://linuxize.com/post/how-to-create-a-sudo-user-on-ubuntu/) to be able to set the root password.

To enable root account in Ubuntu, run the following command:

```text
sudo passwd root
```

You will be prompted to enter and confirm the new root password:

```text
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
```

The password is not shown on the screen when you type it.

That’s it! You have successfully enabled the root account. You can now log in to your Ubuntu machine as user root using the new password.

## Disable Root User Account in Ubuntu [\#](https://linuxize.com/post/how-to-enable-and-disable-root-user-account-in-ubuntu/#disable-root-user-account-in-ubuntu) <a id="disable-root-user-account-in-ubuntu"></a>

If you previously enabled the root user in Ubuntu and now you want to disable it, set the root password to expire.

To disable the root account password, use the following command:

```text
sudo passwd -l root
```

## Conclusion [\#](https://linuxize.com/post/how-to-enable-and-disable-root-user-account-in-ubuntu/#conclusion) <a id="conclusion"></a>

To enable the root user account in Ubuntu, all you need to do is to set the root password.

When setting the password, make sure you’re using a strong and unique password. Having a strong password is the most important aspect of the security of your account. Often a strong password has at least 16 characters, at least one uppercase letter, one lowercase letter, one number, and one special character.

If you have any questions or feedback, feel free to leave a comment.

