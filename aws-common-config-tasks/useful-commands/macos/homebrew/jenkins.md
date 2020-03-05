# Jenkins

  


√ Library % brew services start jenkins

==&gt; Successfully started \`jenkins\` \(label: homebrew.mxcl.jenkins\)

√ Library % cd -lah /usr/local/opt/  

cd: string not in pwd: -lah

?1 Library % cd /usr/local/opt/ 

√ opt % sudo vim jenkins/homebrew.mxcl.jenkins.plist

We want the Jenkins web interface to be accessible from anywhere \(not just on the local machine\), so we’re going to open up the config file:

1. sudo nano /usr/local/opt/jenkins-lts/homebrew.mxcl.jenkins-lts.plist

Find this line:

1. &lt;string&gt;--httpListenAddress=127.0.0.1&lt;/string&gt;

And change it to:

1. &lt;string&gt;--httpListenAddress=0.0.0.0&lt;/string&gt;

\(to exit out of nano after making the change, hit Ctrl+X, hit Y to save the changes, and hit Enter\)

Let’s start Jenkins and set it to run automatically when the system is rebooted:

```text
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>homebrew.mxcl.jenkins</string>
    <key>ProgramArguments</key>
    <array>
      <string>/usr/libexec/java_home</string>
      <string>-v</string>
      <string>1.8</string>
      <string>--exec</string>
      <string>java</string>
      <string>-Dmail.smtp.starttls.enable=true</string>
      <string>-jar</string>
      <string>/usr/local/opt/jenkins/libexec/jenkins.war</string>
      <string>--httpListenAddress=127.0.0.1</string>
      <string>--httpPort=8080</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
  </dict>
</plist>
```

my example setup:

```text
 <string>--httpListenAddress=0.0.0.0</string>
      <string>--httpPort=8090</string>
```

```text
opt % cat /Volumes/iXMAIN/iXXCenter/iXUsers/ixx/.jenkins/secrets/initialAdminPassword
d10e0f1ba1644a09a927037b69ec432a
```

## Create First Admin User

| Username: | ixx |
| :--- | :--- |
| Password: | ixxadmin |
| Confirm password: | ixxadmin |
| Full name: | ixx techie |
| E-mail address: | ixx@email.com |



## Instance Configuration

| Jenkins URL: |  |
| :--- | :--- |
| The Jenkins URL is used to provide the root URL for absolute links to various Jenkins resources. That means this value is required for proper operation of many Jenkins features including email notifications, PR status updates, and the `BUILD_URL` environment variable provided to build steps. |  |

```text

```

  
`p.p1 {margin: 0.0px 0.0px 0.0px 0.0px; font: 24.0px Monaco; color: #f2f2f2; background-color: #000000; background-color: rgba(0, 0, 0, 0.85)}  
p.p2 {margin: 0.0px 0.0px 0.0px 0.0px; font: 24.0px Monaco; color: #ffffff; background-color: #000000; background-color: rgba(0, 0, 0, 0.85)}  
p.p3 {margin: 0.0px 0.0px 0.0px 0.0px; font: 24.0px Monaco; color: #f2f2f2; background-color: #000000; background-color: rgba(0, 0, 0, 0.85); min-height: 32.0px}  
span.s1 {font-variant-ligatures: no-common-ligatures}  
span.s2 {text-decoration: underline ; font-variant-ligatures: no-common-ligatures}  
span.s3 {font-variant-ligatures: no-common-ligatures; color: #400bd9}  
span.s4 {font-variant-ligatures: no-common-ligatures; color: #f2f2f2}  
span.s5 {font-variant-ligatures: no-common-ligatures; color: #2fb41d}  
span.Apple-tab-span {white-space:pre}`  


`% brew info jenkins`          

`jenkins: stable 2.223, HEAD`

`Extendable open source continuous integration server`

`https://jenkins.io/`

`/usr/local/Cellar/jenkins/2.223 (6 files, 63.2MB) *`

  `Built from source on 2020-03-04 at 21:30:40`

`From: https://github.com/Homebrew/homebrew-core/blob/master/Formula/jenkins.rb`

`==> Requirements`

`Required: java = 1.8 ✔`

`==> Options`

`--HEAD`

 `Install HEAD version`

`==> Caveats`

`Note: When using launchctl the port will be 8080.`

`To have launchd start jenkins now and restart at login:`

  `brew services start jenkins`

`Or, if you don't want/need a background service you can just run:`

  `jenkins`

`==> Analytics`

`install: 6,121 (30 days), 18,905 (90 days), 71,698 (365 days)`

`install-on-request: 5,894 (30 days), 18,192 (90 days), 68,388 (365 days)`

`build-error: 0 (30 days)`



Sample commands:

* Install the latest LTS version: `brew install jenkins-lts`
* Install a specific LTS version: `brew install jenkins-lts@YOUR_VERSION`
* Start the Jenkins service: `brew services start jenkins-lts`
* Restart the Jenkins service: `brew services restart jenkins-lts`
* Update the Jenkins version: `brew upgrade jenkins-lts`

After starting the Jenkins service, browse to http://localhost:8080 and follow the instructions to complete the installation. Also see the external materials for installation guidelines. For example, [this blogpost ](https://www.macminivault.com/installing-jenkins-on-macos/)describes the installation process.  


## Installing Jenkins on macOS





### Install Prerequisites

### Install Jenkins and Config

### Local folder - create new folder / change your home directory

* copy .jenkins content to my new home folder
* change the environment variable:

export JENKINS\_HOME=/Volumes/iXMAIN/iXXCenter/iXX-REPOs/iXX-JENKINS/jenkins-home

###  enable CLI - setup and config

* enable security \(management &gt; global security\)
  * [http://localhost:8090/cli/](http://localhost:8090/cli/)
* test your jarfile



```text
√ ~ % ls -lah | grep jenkins | cd .jenkins 
(pwd now: ~/.jenkins)
√ .jenkins % 
```

Aug 24, 2018![Installing Jenkins on macOS](https://www.macminivault.com/wp-content/uploads/jenkins-logo-no_text.png)

Jenkins is Continuous Integration automation control software that allows developers to automate repetitive parts of the software development process. While Jenkins can be installed on many operating systems, this guide will focus on the macOS install process.

This guide assumes you have a fresh install of the latest macOS along with Xcode, and that you don’t already have a Jenkins master server. In a future guide, we will add Jenkins slave servers to the setup.

There are a few ways to install Jenkins on macOS – we’re going to install it using a package manager for macOS called Homebrew. If Homebrew is already installed then skip the next step \(check by running “brew -v” in Terminal\).

Let’s install Homebrew by opening Terminal and entering the following command \(this command is all one line\):

1. /usr/bin/ruby -e "$\(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install\)"

The installer will give you a list of things it’s going to do, just press enter and Homebrew will be installed.

Now that you have Homebrew installed, you can type check to see if there are any recommendations for your setup:

1. brew doctor
2. Your system is ready to brew.

For example, you may have an outdated version of Xcode, in which case you may want to upgrade that:

1. $ brew doctor
2. Please note that these warnings are just used to help the Homebrew maintainers
3. with debugging if you file an issue. If everything you use Homebrew for is
4. working fine: please don't worry and just ignore them. Thanks!
5. 6. Warning: Your Xcode \(8.0\) is outdated.
7. Please update to Xcode 9.4 \(or delete it\).
8. Xcode can be updated from the App Store.

Before installing Jenkins, we need to install a specific version of Java required by Jenkins – it may ask you for your password to set permissions properly:

1. $ brew cask install java8
2. ==&gt; Tapping homebrew/cask
3. Cloning into '/usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask'...
4. remote: Counting objects: 4132, done.
5. remote: Compressing objects: 100% \(4121/4121\), done.
6. remote: Total 4132 \(delta 27\), reused 601 \(delta 8\), pack-reused 0
7. Receiving objects: 100% \(4132/4132\), 1.30 MiB \| 10.54 MiB/s, done.
8. Resolving deltas: 100% \(27/27\), done.
9. Tapped 1 command and 4034 casks \(4,141 files, 4.1MB\).
10. ==&gt; Caveats
11. This Cask makes minor modifications to the JRE to prevent issues with
12. packaged applications, as discussed here:
13. 14.  https://bugs.eclipse.org/bugs/show\_bug.cgi?id=411361
15. 16. If your Java application still asks for JRE installation, you might need
17. to reboot or logout/login.
18. 19. Installing java8 means you have AGREED to the license at
20.  https://www.oracle.com/technetwork/java/javase/terms/license/index.html
21. 22. ==&gt; Satisfying dependencies
23. ==&gt; Downloading http://download.oracle.com/otn-pub/java/jdk/8u181-b13/96a7b8442f
24. ==&gt; Downloading from https://edelivery.oracle.com/otn-pub/java/jdk/8u181-b13/96a
25. \#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\# 100.0%
26. ==&gt; Verifying checksum for Cask java8
27. ==&gt; Installing Cask java8
28. ==&gt; Creating Caskroom at /usr/local/Caskroom
29. ==&gt; We'll set permissions properly so we won't need sudo in the future.
30. Password:
31. ==&gt; Running installer for java8; your password may be necessary.
32. ==&gt; Package installers may write to any location; options such as --appdir are i
33. installer: Package name is JDK 8 Update 181
34. installer: Installing at base path /
35. installer: The install was successful.
36. 🍺 java8 was successfully installed!

Now we can install Jenkins – we’re going to install the LTS \(long-term support version, which is typically more stable\):

1. $ brew install jenkins-lts
2. ==&gt; Downloading http://mirrors.jenkins.io/war-stable/2.121.3/jenkins.war
3. ==&gt; Downloading from http://ftp-chi.osuosl.org/pub/jenkins/war-stable/2.121.3/je
4. \#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\# 100.0%
5. ==&gt; jar xvf jenkins.war
6. ==&gt; Caveats
7. Note: When using launchctl the port will be 8080.
8. 9. To have launchd start jenkins-lts now and restart at login:
10.  brew services start jenkins-lts
11. Or, if you don't want/need a background service you can just run:
12.  jenkins-lts
13. ==&gt; Summary
14. 🍺 /usr/local/Cellar/jenkins-lts/2.121.3: 7 files, 74.5MB, built in 18 seconds

We want the Jenkins web interface to be accessible from anywhere \(not just on the local machine\), so we’re going to open up the config file:

1. sudo nano /usr/local/opt/jenkins-lts/homebrew.mxcl.jenkins-lts.plist

Find this line:

1. &lt;string&gt;--httpListenAddress=127.0.0.1&lt;/string&gt;

And change it to:

1. &lt;string&gt;--httpListenAddress=0.0.0.0&lt;/string&gt;

\(to exit out of nano after making the change, hit Ctrl+X, hit Y to save the changes, and hit Enter\)

Let’s start Jenkins and set it to run automatically when the system is rebooted:

1. $ brew services start jenkins-lts
2. ==&gt; Tapping homebrew/services
3. Cloning into '/usr/local/Homebrew/Library/Taps/homebrew/homebrew-services'...
4. remote: Counting objects: 14, done.
5. remote: Compressing objects: 100% \(10/10\), done.
6. remote: Total 14 \(delta 0\), reused 7 \(delta 0\), pack-reused 0
7. Unpacking objects: 100% \(14/14\), done.
8. Tapped 1 command \(43 files, 55.2KB\).
9. ==&gt; Successfully started \`jenkins-lts\` \(label: homebrew.mxcl.jenkins-lts\)

The rest of the configuration will mostly be done in a browser on the local machine. Open up Safari and visit http://localhost:8080 , where we will see a screen like this:

![](https://www.macminivault.com/wp-content/uploads/unlock_jenkins.png)

Grab the red highlighted text and in Terminal use the ‘cat’ command to display the initial password:

1. $ cat /Users/administrator/.jenkins/secrets/initialAdminPassword
2. fff69c0883fb4cdb9aa85bbd72dd2fd8

Copy that password and paste it into the Unlock Jenkins page. We’re done with Terminal, feel free to close it.

We can now Customize Jenkins and install some plugins. For now we’re going to choose _Install suggested plugins_.

![](https://www.macminivault.com/wp-content/uploads/customize_jenkins.png)

The installer now downloads and installs the plugins:

![](https://www.macminivault.com/wp-content/uploads/jenkins_getting_started.png)

Create an admin user and Save and Continue:

![](https://www.macminivault.com/wp-content/uploads/jenkins_create_admin.png)

Set the URL that users will be using to log in to Jenkins. If users will be connecting to the server remotely, it’s best to set up an A record \(like jenkins.yourdomain.com\) and set the Jenkins URL to **http://jenkins.yourdomain.com:8080.** Click Save and Finish:

![](https://www.macminivault.com/wp-content/uploads/jenkins_url.png)

Setup is complete – click Start using Jenkins.

![](https://www.macminivault.com/wp-content/uploads/jenkins_setup_complete.png)

The rest of the configuration will be done within the Jenkins web interface. You can now create jobs, manage Jenkins and install new plugins, and add new users.

![](https://www.macminivault.com/wp-content/uploads/jenkins_screenshot.png)

#### How to Start / Restart Jenkins on macOS

To start Jenkins and make sure it runs after a reboot:

1. brew services start jenkins-lts

To restart the Jenkins service and make sure it runs after a reboot:

1. brew services restart jenkins-lts

Note: If you didn’t install the LTS version of Jenkins, don’t include the “-lts” portion of the above commands.

