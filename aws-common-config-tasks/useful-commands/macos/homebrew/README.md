# Homebrew

## How to Uninstall Packages with Homebrew

Jul 29, 2018 - [4 Comments](https://osxdaily.com/2018/07/29/uninstall-packages-homebrew-mac/#comments)

![How to uninstall with Homebrew](https://cdn.osxdaily.com/wp-content/uploads/2018/07/homebrew-mac-610x338.jpg)

If you have [installed Homebrew on a Mac](https://osxdaily.com/2018/03/07/how-install-homebrew-mac-os/) to use as a package manager for various unix and command line utilities, you’ve probably also installed a handful of [packages deemed useful](https://osxdaily.com/2018/03/26/best-homebrew-packages-mac/) to you. But what if you no longer need one, and you want to remove a particular Homebrew package?

It turns out that uninstalling packages / formula with Homebrew is very easy, and uninstalling and removing packages from Homebrew is just as easy as installing them in the first place.

  
To be clear, we’re not talking about uninstalling Homebrew itself, we’re just talking about removing particular packages from Homebrew.

### How to Uninstall & Remove Homebrew Packages

The proper way to remove a Homebrew package is with the uninstall or remove command.

The uninstall Homebrew package command looks like this:

`brew uninstall packageName`

The remove Homebrew package command looks like this:

`brew remove packageName`

As you may have guessed by now, the remove and uninstall commands are exactly the same, and get the same result; the removal of the Homebrew package.

For example, to remove and uninstall Telnet \(assuming you [installed telnet on the Mac](https://osxdaily.com/2018/07/18/get-telnet-macos/) with Homebrew anyway\), you would use the following command string:

`brew uninstall telnet`

Or you can use the remove command for the same effect:

`brew remove telnet`

Removing a package from Homebrew is quick, as there is no need to download anything, it just deletes the Homebrew package from the Mac.

You can confirm the package was removed by trying to run the command again, or by checking [where Homebrew packages are installed to](https://osxdaily.com/2018/07/05/where-homebrew-packages-installed-location-mac/) and you will find the package you removed is no longer there.

#### Additional Homebrew Package Uninstall Options

There are two flags you can pass to the Homebrew uninstall command as well; –force and –ignore-dependencies.

The –force flag \(or -f\) will forcibly remove the package along with deleting all versions of that package / formula.

The –ignore-dependencies flag does just what it sounds like, it will ignore dependencies for the formula in question when uninstalling the designated package.

#### Managing Dependencies when Uninstalling Homebrew Packages

One thing to be mindful of when removing and uninstalling packages from Homebrew is that if the package being uninstalled has dependencies that are in use by another package or formula, then that may break it causing the secondary package to no longer work correctly. Perhaps the simplest way to prevent that is to use the optional –ignore-dependencies flag. For example:

`brew uninstall --ignore-dependencies telnet`

If you are not sure what dependencies exist with a particular Homebrew package, you can use the deps command to find that out:

`brew deps packageName`

For example, if you [installed python3 on the Mac](https://osxdaily.com/2018/06/13/how-install-update-python-3x-mac/) using the Homebrew approach, which has a fair amount of dependencies, running that command would look something like the following:

`% brew deps python3  
gdbm  
openssl  
readline  
sqlite  
xz`

Since many other packages also use those dependencies, if you were to remove python3 you’d almost certainly want to issue the –ignore-dependencies flag. The same applies to [node.js and npm](https://osxdaily.com/2018/06/29/how-install-nodejs-npm-mac/), and many other [popular Homebrew packages](https://osxdaily.com/2018/03/26/best-homebrew-packages-mac/).

Do you know of any other methods or tips related to uninstalling Homebrew packages and formula? Share with us in the comments below!

