---
description: in Ubuntu
---

# Changing Root Password

![](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVR42mP8+PXHfwAJnAPfCuZXlQAAAABJRU5ErkJggg==)

The root user \(or superuser\) is a special user account that is present on all Linux and Unix-like systems. It has full access to every command and any resource on the system without any restrictions.

If you are coming to Ubuntu from another Linux distribution, you may wonder what the default root password is or how to change the root password. By default, in Ubuntu, the root user account is disabled for security reasons.

This tutorial explains how to temporally change to the root user account and how to set the root password on Ubuntu systems.

## Temporary Switching to root [\#](https://linuxize.com/post/how-to-change-root-password-in-ubuntu/#temporary-switching-to-root) <a id="temporary-switching-to-root"></a>

Ubuntu users are encouraged to perform system administrative tasks by granting sudo privileges to regular users. Sudo allows authorized users to run programs as another user, usually the root user.

The initial user created by the Ubuntu installer is already a member of the sudo group. The chances are that the user you are logged in as is already granted with administrative privileges.

To temporarily elevate root user privileges, run the command prefixed with [`sudo`](https://linuxize.com/post/sudo-command-in-linux/):

```text
sudo command-name
```

The first time you use sudo in a session, you will be prompted to enter the user password.

To temporally switch to the root account in the current login session, you can use either the [`sudo su`](https://linuxize.com/post/su-command-in-linux/) or `sudo -i` command and enter the user password:

```text
sudo su -
```

Run the `whoami` command to verify that the user is changed:

```text
whoami
```

```text
root
```

## Changing Root Password [\#](https://linuxize.com/post/how-to-change-root-password-in-ubuntu/#changing-root-password) <a id="changing-root-password"></a>

The root user is disabled, but that doesn’t mean that the root account has been removed. Logging in as root is not possible because no password has been set for the root account.

If for some reason, you need to [enable the root account](https://linuxize.com/post/how-to-enable-and-disable-root-user-account-in-ubuntu/), all you need to do is to set a password for the root user. In Ubuntu, you can set or change the password of a user account with the [`passwd`](https://linuxize.com/post/how-to-change-user-password-in-ubuntu/) command.

To change the password of the root user in Ubuntu, run the following command as a [sudo user](https://linuxize.com/post/how-to-create-a-sudo-user-on-ubuntu/):

```text
sudo passwd root
```

You will be prompted to enter and confirm the new root password.

When setting the password, make sure you’re using a unique and robust password. Having a strong password is the most important aspect of the security of your account. Often a strong password has at least 16 characters, at least one uppercase letter, one lowercase letter, one number, and one special character.

The password is not shown on the screen when you type it.

```text
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
```

That’s it! The root password has been changed.

You can now [log in to your Ubuntu system](https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-18-04/) as root using the new password.

## Conclusion [\#](https://linuxize.com/post/how-to-change-root-password-in-ubuntu/#conclusion) <a id="conclusion"></a>

By default, in Ubuntu, the root account has no password set. The recommended approach is to use the `sudo` command to run commands with root-level privileges.

To be able to log in as root directly, you’ll need to set the root password.

If you have any questions or feedback, feel free to leave a comment.

