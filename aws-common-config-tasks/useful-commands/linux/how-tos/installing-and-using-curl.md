---
description: on Ubuntu 18.04
---

# Installing and Using Curl

![](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVR42mP8+PXHfwAJnAPfCuZXlQAAAABJRU5ErkJggg==)

You are following a tutorial in which a file is downloaded using the `curl` utility. You run the command and you get the following error message _`curl command not found`_. There’s nothing to worry about, this simply means that the `curl` package is not installed on your Ubuntu machine.

Curl is a command line tool that allows you to transfer data from or to a remote server. With `curl`, you can download or upload data using one of the supported protocols including HTTP, HTTPS, [SCP](https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/), [SFTP](https://linuxize.com/post/how-to-use-linux-sftp-command-to-transfer-files/), and [FTP](https://linuxize.com/post/how-to-use-linux-ftp-command-to-transfer-files/).

In this tutorial, we will show you how to install [Curl](https://curl.haxx.se/) on Ubuntu 18.04.

## Installing Curl on Ubuntu [\#](https://linuxize.com/post/how-to-install-and-use-curl-on-ubuntu-18-04/#installing-curl-on-ubuntu) <a id="installing-curl-on-ubuntu"></a>

Curl package is included in the default Ubuntu 18.04 repositories. The installation is pretty straightforward, just type:

```text
sudo apt install curl
```

To verify that `curl` has been installed, type `curl` in your terminal, and press `Enter`:

```text
curl
```

The output will look something like this:

```text
curl: try 'curl --help' or 'curl --manual' for more information
```

That’s it! At this point, you have successfully installed curl on your Ubuntu system.

## Using Curl [\#](https://linuxize.com/post/how-to-install-and-use-curl-on-ubuntu-18-04/#using-curl) <a id="using-curl"></a>

In its simplest form when used without any option, Curl will display the resource specified in the \[url\] to the standard output.

For example, the command below will print the source-code of the `example.com` homepage in your terminal window:

```text
curl https://example.com
```

To download a file with Curl you can use either the `-o` or `-O` options.

Lowercase `-o` allows you to specify the name of the file you are downloading:

```text
curl -o linux.tar.xz https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.0.5.tar.xz
```

Uppercase `-O` will save the file with its original filename:

```text
curl -O https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.0.5.tar.xz
```

Another useful feature of Curl is its ability to fetch only the HTTP headers of the specified URL:

```text
curl -I https://www.ubuntu.com/
```

```text
HTTP/1.1 200 OK
Date: Tue, 02 Apr 2019 20:47:44 GMT
Server: gunicorn/19.9.0
Strict-Transport-Security: max-age=15768000
X-Hostname: juju-prod45-ubuntu-website-machine-15
Content-Type: text/html; charset=utf-8
Age: 42
X-Cache: HIT from privet.canonical.com
X-Cache-Lookup: HIT from privet.canonical.com:80
Via: 1.1 privet.canonical.com (squid/3.5.12)
```

With `curl` you can also download files from password protected FTP servers:

```text
curl -u FTP_USERNAME:FTP_PASSWORD ftp://ftp.example.com/file.tar.gz
```

## Conclusion [\#](https://linuxize.com/post/how-to-install-and-use-curl-on-ubuntu-18-04/#conclusion) <a id="conclusion"></a>

You have successfully installed Curl on your Ubuntu system. For more information about the most commonly used curl options, check [Curl Command Examples](https://linuxize.com/post/curl-command-examples/).

If you have any questions or feedback, feel free to leave a comment.

