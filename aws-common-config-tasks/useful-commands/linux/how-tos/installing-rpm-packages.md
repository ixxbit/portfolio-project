---
description: on Ubuntu
---

# Installing RPM packages

The Ubuntu repositories contain thousands of deb packages which can be installed from the Ubuntu Software Center or by using the [`apt`](https://linuxize.com/post/how-to-use-apt-command/) command line utility. Deb is the installation package format used by all Debian based distributions including Ubuntu. Some packages are not available in the standard Ubuntu repositories but it can be easily installed by enabling the appropriate source.

In most cases when the software vendor does not provide a repository they will have a download page from where you can download and install the deb package or download and compile the software from sources.

Although not so often, some software may be distributed only as an RPM package. RPM is a package format used by Red Hat and its derivatives such as CentOS. Luckily, there is a tool called alien that allows us to install an RPM file on Ubuntu or to convert an RPM package file into a Debian package file.

## Before you Begin [\#](https://linuxize.com/post/install-rpm-packages-on-ubuntu/#before-you-begin) <a id="before-you-begin"></a>

This is not the recommended way to install software packages in Ubuntu. Whenever possible you should prefer installing software from the Ubuntu repositories.

Not all RPM packages can be installed on Ubuntu. Installing RPM packaged on Ubuntu may lead to package dependency conflicts.

You should never use this method to replace or update important system packages, like libc, systemd, or other services and libraries that are essential for the proper functioning of your system. Doing this may lead to errors and system instability.

## Install Alien [\#](https://linuxize.com/post/install-rpm-packages-on-ubuntu/#install-alien) <a id="install-alien"></a>

Alien is a tool that supports conversion between Red Hat rpm, Debian deb, Stampede slp, Slackware tgz, and Solaris pkg file formats.

Before installing the alien package make sure the Universe repository is enabled on your system:

```text
sudo add-apt-repository universe
```

Once the repository is enabled update the packages index and install the alien package with:

```text
sudo apt update sudo apt install alien
```

The command above will also install the necessary build tools.

## Converting and Installing an RPM package [\#](https://linuxize.com/post/install-rpm-packages-on-ubuntu/#converting-and-installing-an-rpm-package) <a id="converting-and-installing-an-rpm-package"></a>

To convert a package from RPM to DEB format use the alien command followed by the RPM package name:

```text
sudo alien package_name.rpm
```

Depending on the package size the conversion may take some time. In most cases, you will see warning messages printed on your screen. If the package is successfully converted the output will indicate that the DEB package is generated:

```text
package_name.deb generated
```

To [install the deb package](https://linuxize.com/post/how-to-install-deb-packages-on-ubuntu/), you can either use the `dpkg` or [`apt`](https://linuxize.com/post/how-to-use-apt-command/) utility:

```text
sudo dpkg -i package_name.deb
```

```text
sudo apt install ./package_name.deb
```

The package should now be installed, assuming it’s compatible with your system and all dependencies are met.

You’ll need to be logged in as a [user with sudo access](https://linuxize.com/post/how-to-create-a-sudo-user-on-ubuntu/) to be able to install packages on your Ubuntu system.

## Installing an RPM package directly [\#](https://linuxize.com/post/install-rpm-packages-on-ubuntu/#installing-an-rpm-package-directly) <a id="installing-an-rpm-package-directly"></a>

Instead of converting and then installing the package you can use the `-i` option that will tell alien to install the RPM package directly.

```text
sudo alien -i package_name.rpm
```

The command above will automatically generate and installed the package and remove the package file after it has been installed.

## Conclusion [\#](https://linuxize.com/post/install-rpm-packages-on-ubuntu/#conclusion) <a id="conclusion"></a>

In this tutorial, you learned how to install RPM packages on Ubuntu.

If you have any questions or feedback, feel free to leave a comment.

