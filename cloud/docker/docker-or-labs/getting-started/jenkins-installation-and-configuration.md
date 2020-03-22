---
description: Mac and Linux
---

# Jenkins: Installation and Configuration



**On macOS and Linux**

1. Open up a terminal window.
2. Create a [bridge network](https://docs.docker.com/network/bridge/) in Docker using the following [`docker network create`](https://docs.docker.com/engine/reference/commandline/network_create/) command:

   ```text
   docker network create jenkins
   ```

3. Create the following [volumes](https://docs.docker.com/storage/volumes/) to share the Docker client TLS certificates needed to connect to the Docker daemon and persist the Jenkins data using the following [`docker volume create`](https://docs.docker.com/engine/reference/commandline/volume_create/) commands:

   ```text
   docker volume create jenkins-docker-certs
   docker volume create jenkins-data
   ```

4. In order to execute Docker commands inside Jenkins nodes, download and run the `docker:dind` Docker image using the following [`docker container run`](https://docs.docker.com/engine/reference/commandline/container_run/) command:

   ```text
   docker container run \
     --name jenkins-docker \
     --rm \
     --detach \
     --privileged \
     --network jenkins \
     --network-alias docker \
     --env DOCKER_TLS_CERTDIR=/certs \
     --volume jenkins-docker-certs:/certs/client \
     --volume jenkins-data:/var/jenkins_home \
     --publish 2376:2376 \
     docker:dind
   ```

   |  | \( _Optional_ \) Specifies the Docker container name to use for running the image. By default, Docker will generate a unique name for the container. |
   | :--- | :--- |
   |  | \( _Optional_ \) Automatically removes the Docker container \(the instance of the Docker image\) when it is shut down. This contains the Docker image cache used by Docker when invoked from the `jenkinsci/blueocean` container described below. |
   |  | \( _Optional_ \) Runs the Docker container in the background. This instance can be stopped later by running `docker container stop jenkins-docker` and started again with `docker container start jenkins-docker`. See [`docker container`](https://docs.docker.com/engine/reference/commandline/container/) for more container management commands. |
   |  | Running Docker in Docker currently requires privileged access to function properly. This requirement may be relaxed with newer Linux kernel versions. |
   |  | This corresponds with the network created in the earlier step. |
   |  | Makes the Docker in Docker container available as the hostname `docker` within the `jenkins` network. |
   |  | Enables the use of TLS in the Docker server. Due to the use of a privileged container, this is recommended, though it requires the use of the shared volume described below. This environment variable controls the root directory where Docker TLS certificates are managed. |
   |  | Maps the `/certs/client` directory inside the container to a Docker volume named `jenkins-docker-certs` as created above. |
   |  | Maps the `/var/jenkins_home` directory inside the container to the Docker volume named `jenkins-data`as created above. This will allow for other Docker containers controlled by this Docker container’s Docker daemon to mount data from Jenkins. |
   |  | \( _Optional_ \) Exposes the Docker daemon port on the host machine. This is useful for executing `docker`commands on the host machine to control this inner Docker daemon. |
   |  | The `docker:dind` image itself. This image can be downloaded before running by using the command: `docker image pull docker:dind`. |

   **Note:** If copying and pasting the command snippet above does not work, try copying and pasting this annotation-free version here:

   ```text
   docker container run --name jenkins-docker --rm --detach \
     --privileged --network jenkins --network-alias docker \
     --env DOCKER_TLS_CERTDIR=/certs \
     --volume jenkins-docker-certs:/certs/client \
     --volume jenkins-data:/var/jenkins_home \
     --publish 2376:2376 docker:dind
   ```

5. Download the `jenkinsci/blueocean` image and run it as a container in Docker using the following [`docker container run`](https://docs.docker.com/engine/reference/commandline/container_run/) command:

   ```text
   docker container run \
     --name jenkins-blueocean \
     --rm \
     --detach \
     --network jenkins \
     --env DOCKER_HOST=tcp://docker:2376 \
     --env DOCKER_CERT_PATH=/certs/client \
     --env DOCKER_TLS_VERIFY=1 \
     --publish 8080:8080 \
     --publish 50000:50000 \
     --volume jenkins-data:/var/jenkins_home \
     --volume jenkins-docker-certs:/certs/client:ro \
     jenkinsci/blueocean
   ```

   |  | \( _Optional_ \) Specifies the Docker container name for this instance of the `jenkinsci/blueocean` Docker image. This makes it simpler to reference by subsequent `docker container` commands. |
   | :--- | :--- |
   |  | \( _Optional_ \) Automatically removes the Docker container \(which is the instantiation of the `jenkinsci/blueocean` image below\) when it is shut down. This keeps things tidy if you need to quit Jenkins. |
   |  | \( _Optional_ \) Runs the `jenkinsci/blueocean` container in the background \(i.e. "detached" mode\) and outputs the container ID. If you do not specify this option, then the running Docker log for this container is output in the terminal window. |
   |  | Connects this container to the `jenkins` network defined in the earlier step. This makes the Docker daemon from the previous step available to this Jenkins container through the hostname `docker`. |
   |  | Specifies the environment variables used by `docker`, `docker-compose`, and other Docker tools to connect to the Docker daemon from the previous step. |
   |  | Maps \(i.e. "publishes"\) port 8080 of the `jenkinsci/blueocean` container to port 8080 on the host machine. The first number represents the port on the host while the last represents the container’s port. Therefore, if you specified `-p 49000:8080` for this option, you would be accessing Jenkins on your host machine through port 49000. |
   |  | \( _Optional_ \) Maps port 50000 of the `jenkinsci/blueocean` container to port 50000 on the host machine. This is only necessary if you have set up one or more JNLP-based Jenkins agents on other machines, which in turn interact with the `jenkinsci/blueocean` container \(acting as the "master" Jenkins server, or simply "Jenkins master"\). JNLP-based Jenkins agents communicate with the Jenkins master through TCP port 50000 by default. You can change this port number on your Jenkins master through the [Configure Global Security](https://jenkins.io/doc/book/managing/security/) page. If you were to change your Jenkins master’s **TCP port for JNLP agents** value to 51000 \(for example\), then you would need to re-run Jenkins \(via this `docker run …​`command\) and specify this "publish" option with something like `--publish 52000:51000`, where the last value matches this changed value on the Jenkins master and the first value is the port number on the Jenkins master’s host machine through which the JNLP-based Jenkins agents communicate \(to the Jenkins master\) - i.e. 52000. Note that WebSocket agents in Jenkins 2.217 do not need this configuration. |
   |  | Maps the `/var/jenkins_home` directory in the container to the Docker [volume](https://docs.docker.com/engine/admin/volumes/volumes/) with the name `jenkins-data`. Instead of mapping the `/var/jenkins_home` directory to a Docker volume, you could also map this directory to one on your machine’s local file system. For example, specifying the option `--volume $HOME/jenkins:/var/jenkins_home` would map the container’s `/var/jenkins_home`directory to the `jenkins` subdirectory within the `$HOME` directory on your local machine, which would typically be `/Users/<your-username>/jenkins` or `/home/<your-username>/jenkins`. Note that if you change the source volume or directory for this, the volume from the `docker:dind` container above needs to be updated to match this. |
   |  | Maps the `/certs/client` directory to the previously created `jenkins-docker-certs` volume. This makes the client TLS certificates needed to connect to the Docker daemon available in the path specified by the `DOCKER_CERT_PATH` environment variable. |
   |  | The `jenkinsci/blueocean` Docker image itself. If this image has not already been downloaded, then this `docker container run` command will automatically download the image for you. Furthermore, if any updates to this image were published since you last ran this command, then running this command again will automatically download these published image updates for you. **Note:** This Docker image could also be downloaded \(or updated\) independently using the [`docker image pull`](https://docs.docker.com/engine/reference/commandline/image_pull/) command: `docker image pull jenkinsci/blueocean` |

   **Note:** If copying and pasting the command snippet above does not work, try copying and pasting this annotation-free version here:

   ```text
   docker container run --name jenkins-blueocean --rm --detach \
     --network jenkins --env DOCKER_HOST=tcp://docker:2376 \
     --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 \
     --volume jenkins-data:/var/jenkins_home \
     --volume jenkins-docker-certs:/certs/client:ro \
     --publish 8080:8080 --publish 50000:50000 jenkinsci/blueocean
   ```

6. Proceed to the [Post-installation setup wizard](https://jenkins.io/doc/book/installing/#setup-wizard).

**On Windows**

The Jenkins project provides a Linux container image, not a Windows container image. Be sure that your Docker for Windows installation is configured to run `Linux Containers` rather than `Windows Containers`. See the Docker documentation for instructions to [switch to Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers). Once configured to run `Linux Containers`, the steps are:

1. Open up a command prompt window.
2. Create a [bridge network](https://docs.docker.com/network/bridge/) in Docker using the following [`docker network create`](https://docs.docker.com/engine/reference/commandline/network_create/) command:

   ```text
   docker network create jenkins
   ```

3. Create the following [volumes](https://docs.docker.com/storage/volumes/) to share the Docker client TLS certificates needed to connect to the Docker daemon and persist the Jenkins data using the following [`docker volume create`](https://docs.docker.com/engine/reference/commandline/volume_create/) commands:

   ```text
   docker volume create jenkins-docker-certs
   docker volume create jenkins-data
   ```

4. In order to execute Docker commands inside Jenkins nodes, download and run the `docker:dind` Docker image using the following [`docker container run`](https://docs.docker.com/engine/reference/commandline/container_run/) command:

   ```text
   docker container run --name jenkins-docker --rm --detach ^
     --privileged --network jenkins --network-alias docker ^
     --env DOCKER_TLS_CERTDIR=/certs ^
     --volume jenkins-docker-certs:/certs/client ^
     --volume jenkins-data:/var/jenkins_home ^
     docker:dind
   ```

5. Download the `jenkinsci/blueocean` image and run it as a container in Docker using the following [`docker container run`](https://docs.docker.com/engine/reference/commandline/container_run/) command:

   ```text
   docker container run --name jenkins-blueocean --rm --detach ^
     --network jenkins --env DOCKER_HOST=tcp://docker:2376 ^
     --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 ^
     --volume jenkins-data:/var/jenkins_home ^
     --volume jenkins-docker-certs:/certs/client:ro ^
     --publish 8080:8080 --publish 50000:50000 jenkinsci/blueocean
   ```

   For an explanation of each of these options, refer to the [macOS and Linux](https://jenkins.io/doc/book/installing/#on-macos-and-linux) instructions above.

6. Proceed to the [Post-installation setup wizard](https://jenkins.io/doc/book/installing/#setup-wizard).

**Accessing the Jenkins/Blue Ocean Docker container**

If you have some experience with Docker and you wish or need to access the `jenkinsci/blueocean` container through a terminal/command prompt using the [`docker container exec`](https://docs.docker.com/engine/reference/commandline/container_exec/) command, you can add an option like `--name jenkins-blueocean` \(with the [`docker container run`](https://docs.docker.com/engine/reference/commandline/container_run/) above\), which would give the `jenkinsci/blueocean`container the name "jenkins-blueocean".

This means you could access the container \(through a separate terminal/command prompt window\) with a `docker container exec` command like:

`docker container exec -it jenkins-blueocean bash`

**Accessing the Jenkins console log through Docker logs**

There is a possibility you may need to access the Jenkins console log, for instance, when [Unlocking Jenkins](https://jenkins.io/doc/book/installing/#unlocking-jenkins) as part of the [Post-installation setup wizard](https://jenkins.io/doc/book/installing/#setup-wizard).

If you did not specify the detached mode option `--detach` with the `docker container run …​` command [above](https://jenkins.io/doc/book/installing/#downloading-and-running-jenkins-in-docker), then the Jenkins console log is easily accessible through the terminal/command prompt window from which you ran this Docker command.

Otherwise, you can access the Jenkins console log through the [Docker logs](https://docs.docker.com/engine/reference/commandline/container_logs/) of the `jenkinsci/blueocean` container using the following command:

`docker container logs <docker-container-name>`

Your `<docker-container-name>` can be obtained using the [`docker container ls`](https://docs.docker.com/engine/reference/commandline/container_ls/) command. If you specified the  
`--name jenkins-blueocean` option in the `docker container run …​` command above \(see also [Accessing the Jenkins/Blue Ocean Docker container](https://jenkins.io/doc/book/installing/#accessing-the-jenkins-blue-ocean-docker-container)\), you can simply use the `docker container logs` command:

`docker container logs jenkins-blueocean`

**Accessing the Jenkins home directory**

There is a possibility you may need to access the Jenkins home directory, for instance, to check the details of a Jenkins build in the `workspace` subdirectory.

If you mapped the Jenkins home directory \(`/var/jenkins_home`\) to one on your machine’s local file system \(i.e. in the `docker container run …​` command [above](https://jenkins.io/doc/book/installing/#downloading-and-running-jenkins-in-docker)\), then you can access the contents of this directory through your machine’s usual terminal/command prompt.

Otherwise, if you specified the `--volume jenkins-data:/var/jenkins_home` option in the `docker container run …​` command, you can access the contents of the Jenkins home directory through the `jenkinsci/blueocean`container’s terminal/command prompt using the [`docker container exec`](https://docs.docker.com/engine/reference/commandline/container_exec/) command:

`docker container exec -it <docker-container-name> bash`

As mentioned [above](https://jenkins.io/doc/book/installing/#accessing-the-jenkins-console-log-through-docker-logs), your `<docker-container-name>` can be obtained using the [`docker container ls`](https://docs.docker.com/engine/reference/commandline/container_ls/) command. If you specified the  
`--name jenkins-blueocean` option in the `docker container run …​` command above \(see also [Accessing the Jenkins/Blue Ocean Docker container](https://jenkins.io/doc/book/installing/#accessing-the-jenkins-blue-ocean-docker-container)\), you can simply use the `docker container exec` command:

`docker container exec -it jenkins-blueocean bash`

#### WAR file <a id="war-file"></a>

The Web application ARchive \(WAR\) file version of Jenkins can be installed on any operating system or platform that supports Java.

**To download and run the WAR file version of Jenkins:**

1. Download the [latest stable Jenkins WAR file](http://mirrors.jenkins.io/war-stable/latest/jenkins.war) to an appropriate directory on your machine.
2. Open up a terminal/command prompt window to the download directory.
3. Run the command `java -jar jenkins.war`.
4. Browse to `http://localhost:8080` and wait until the **Unlock Jenkins** page appears.
5. Continue on with the [Post-installation setup wizard](https://jenkins.io/doc/book/installing/#setup-wizard) below.

**Notes:**

* Unlike downloading and running Jenkins with Blue Ocean in Docker \([above](https://jenkins.io/doc/book/installing/#docker)\), this process does not automatically install the Blue Ocean features, which would need to installed separately via the [**Manage Jenkins**](https://jenkins.io/doc/book/managing) &gt; [**Manage Plugins**](https://jenkins.io/doc/book/managing/plugins/) page in Jenkins. Read more about the specifics for installing Blue Ocean on the[Getting started with Blue Ocean](https://jenkins.io/doc/book/blueocean/getting-started/) page.
* You can change the port by specifying the `--httpPort` option when you run the `java -jar jenkins.war`command. For example, to make Jenkins accessible through port 9090, then run Jenkins using the command: `java -jar jenkins.war --httpPort=9090`

#### macOS <a id="macos"></a>

* [Installing Jenkins LTS on macOS](https://jenkins.io/download/lts/macos)
* [Installing Jenkins Weekly on macOS](https://jenkins.io/download/weekly/macos)

#### Linux <a id="linux"></a>

**Debian/Ubuntu**

On Debian-based distributions, such as Ubuntu, you can install Jenkins through `apt`.

Recent versions are available in [an apt repository](https://pkg.jenkins.io/debian/). Older but stable LTS versions are in [this apt repository](https://pkg.jenkins.io/debian-stable/).

```text
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
    /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins
```

|  | If you face error "jenkins : Depends: daemon but it is not installable", execute following command after `sudo apt-get update` - |
| :--- | :--- |


This package installation will:

* Setup Jenkins as a daemon launched on start. See `/etc/init.d/jenkins` for more details.
* Create a ‘jenkins’ user to run this service.
* Direct console log output to the file `/var/log/jenkins/jenkins.log`. Check this file if you are troubleshooting Jenkins.
* Populate `/etc/default/jenkins` with configuration parameters for the launch, e.g `JENKINS_HOME`
* Set Jenkins to listen on port 8080. Access this port with your browser to start configuration.

|  | If your `/etc/init.d/jenkins` file fails to start Jenkins, edit the `/etc/default/jenkins` to replace the line `----HTTP_PORT=8080----` with `----HTTP_PORT=8081----` Here, "8081" was chosen but you can put another port available. |
| :--- | :--- |


**Fedora**

You can install Jenkins through `dnf`. You need to add the Jenkins repository from the Jenkins website to the package manager first.

```text
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    http://pkg.jenkins-ci.org/redhat/jenkins.repo
sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
```

Then, you can install Jenkins. The following command also ensures you have java installed.

```text
sudo dnf upgrade && sudo dnf install jenkins java
```

Next, start the Jenkins service.

```text
sudo service jenkins start
sudo chkconfig jenkins on
```

You can check the status of the Jenkins service using this systemctl command:

```text
systemctl status jenkins
```

If everything has been set up correctly, you should see an output like this:

```text
Loaded: loaded (/etc/rc.d/init.d/jenkins; generated)
Active: active (running) since Tue 2018-11-13 16:19:01 +03; 4min 57s ago
...
```

|  | If you have a firewall installed, you must add Jenkins as an exception. You must change `YOURPORT`in the script below to the port you want to use. Port `8080` is the most common. |
| :--- | :--- |


#### Windows <a id="windows"></a>

To install from the website, using the installer:

* [Download the latest package](http://mirrors.jenkins.io/windows/latest)
* Open the package and follow the instructions

#### Other operating systems <a id="other-operating-systems"></a>

**OpenIndiana Hipster**

On a system running [OpenIndiana Hipster](https://www.openindiana.org/) Jenkins can be installed in either the local or global zone using the [Image Packaging System](https://en.wikipedia.org/wiki/Image_Packaging_System) \(IPS\).

|  | Disclaimer: This platform is NOT officially supported by the Jenkins team, use it at your own risk. Packaging and integration described in this section is maintained by the OpenIndiana Hipster team, bundling the generic `jenkins.war` to work in that operating environment. |
| :--- | :--- |


For the common case of running the newest packaged weekly build as a standalone \(Jetty\) server, simply execute:

```text
pkg install jenkins
svcadm enable jenkins
```

The common packaging integration for a standalone service will:

* Create a `jenkins` user to run the service and to own the directory structures under `/var/lib/jenkins`.
* Pull the OpenJDK8 and other packages required to execute Jenkins, including the `jenkins-core-weekly`package with the latest `jenkins.war`.

  |  | Long-Term Support \(LTS\) Jenkins releases currently do not support OpenZFS-based systems, so no packaging is provided at this time. |
  | :--- | :--- |

* Set up Jenkins as an SMF service instance \(`svc:/network/http:jenkins`\) which  can then be enabled with the `svcadm` command demonstrated above.
* Set up Jenkins to listen on port 8080.
* Configure the log output to be managed by SMF at `/var/svc/log/network-http:jenkins.log`.

Once Jenkins is running, consult the log \(`/var/svc/log/network-http:jenkins.log`\) to retrieve the generated administrator password for the initial set up of Jenkins, usually it will be found at `/var/lib/jenkins/home/secrets/initialAdminPassword`. Then navigate to [localhost:8080](http://localhost:8080/) to [complete configuration of the Jenkins instance](https://jenkins.io/doc/book/installing/#setup-wizard).

To change attributes of the service, such as environment variables like `JENKINS_HOME` or the port number used for the Jetty web server, use the `svccfg` utility:

```text
svccfg -s svc:/network/http:jenkins editprop
svcadm refresh svc:/network/http:jenkins
```

You can also refer to `/lib/svc/manifest/network/jenkins-standalone.xml` for more details and comments about currently supported tunables of the SMF service. Note that the `jenkins` user account created by the packaging is specially privileged to allow binding to port numbers under 1024.

The current status of Jenkins-related packages available for the given release of OpenIndiana can be queried with:

```text
pkg info -r '*jenkins*'
```

Upgrades to the package can be performed by updating the entire operating environment with `pkg update`, or specifically for Jenkins core software with:

```text
pkg update jenkins-core-weekly
```

|  | Procedure for updating the package will restart the currently running Jenkins process. Make sure to prepare it for shutdown and finish all running jobs before updating, if needed. |
| :--- | :--- |


**Solaris, OmniOS, SmartOS, and other siblings**

Generally it should suffice to install Java 8 and [download](https://jenkins.io/download) the `jenkins.war` and run it as a standalone process or under an application server such as [Apache Tomcat](https://tomcat.apache.org/).

Some caveats apply:

* Headless JVM and fonts: For OpenJDK builds on minimalized-footprint systems, there may be [issues running the headless JVM](https://wiki.jenkins.io/display/JENKINS/Jenkins+got+java.awt.headless+problem), because Jenkins needs some fonts to render certain pages.
* ZFS-related JVM crashes: When Jenkins runs on a system detected as a `SunOS`, it tries to load integration for advanced ZFS features using the bundled `libzfs.jar` which maps calls from Java to native `libzfs.so`routines provided by the host OS. Unfortunately, that library was made for binary utilities built and bundled by the OS along with it at the same time, and was never intended as a stable interface exposed to consumers. As the forks of Solaris legacy, including ZFS and later the OpenZFS initiative evolved, many different binary function signatures were provided by different host operating systems - and when Jenkins `libzfs.jar` invoked the wrong signature, the whole JVM process crashed. A solution was proposed and integrated in `jenkins.war`since weekly release 2.55 \(and not yet in any LTS to date\) which enables the administrator to configure which function signatures should be used for each function known to have different variants, apply it to their application server initialization options and then run and update the generic `jenkins.war` without further workarounds. See [the libzfs4j Git repository](https://github.com/kohsuke/libzfs4j) for more details, including a script to try and "lock-pick" the configuration needed for your particular distribution \(in particular if your kernel updates bring a new incompatible `libzfs.so`\).

Also note that forks of the OpenZFS initiative may provide ZFS on various BSD, Linux, and macOS distributions. Once Jenkins supports detecting ZFS capabilities, rather than relying on the `SunOS` check, the above caveats for ZFS integration with Jenkins should be considered.

### Post-installation setup wizard <a id="setup-wizard"></a>

After downloading, installing and running Jenkins using one of the procedures above, the post-installation setup wizard begins.

This setup wizard takes you through are a few quick "one-off" steps to unlock Jenkins, customize it with plugins and create the first administrator user through which you can continue accessing Jenkins.

#### Unlocking Jenkins <a id="unlocking-jenkins"></a>

When you first access a new Jenkins instance, you are asked to unlock it using an automatically-generated password.

1. Browse to `http://localhost:8080` \(or whichever port you configured for Jenkins when installing it\) and wait until the **Unlock Jenkins** page appears.

   ![Unlock Jenkins page](https://jenkins.io/doc/book/resources/tutorials/setup-jenkins-01-unlock-jenkins-page.jpg)

2. From the Jenkins console log output, copy the automatically-generated alphanumeric password \(between the 2 sets of asterisks\).

   ![Copying initial admin password](https://jenkins.io/doc/book/resources/tutorials/setup-jenkins-02-copying-initial-admin-password.png)

3. On the **Unlock Jenkins** page, paste this password into the **Administrator password** field and click **Continue**. **Notes:**
   * If you ran Jenkins in Docker in detached mode, you can access the Jenkins console log from the Docker logs \([above](https://jenkins.io/doc/book/installing/#accessing-the-jenkins-console-log-through-docker-logs)\).
   * The Jenkins console log indicates the location \(in the Jenkins home directory\) where this password can also be obtained. This password must be entered in the setup wizard on new Jenkins installations before you can access Jenkins’s main UI. This password also serves as the default admininstrator account’s password \(with username "admin"\) if you happen to skip the subsequent user-creation step in the setup wizard.

#### Customizing Jenkins with plugins <a id="customizing-jenkins-with-plugins"></a>

After [unlocking Jenkins](https://jenkins.io/doc/book/installing/#unlocking-jenkins), the **Customize Jenkins** page appears. Here you can install any number of useful plugins as part of your initial setup.

Click one of the two options shown:

* **Install suggested plugins** - to install the recommended set of plugins, which are based on most common use cases.
* **Select plugins to install** - to choose which set of plugins to initially install. When you first access the plugin selection page, the suggested plugins are selected by default.

|  | If you are not sure what plugins you need, choose **Install suggested plugins**. You can install \(or remove\) additional Jenkins plugins at a later point in time via the [**Manage Jenkins**](https://jenkins.io/doc/book/managing) &gt; [**Manage Plugins**](https://jenkins.io/doc/book/managing/plugins/) page in Jenkins. |
| :--- | :--- |


The setup wizard shows the progression of Jenkins being configured and your chosen set of Jenkins plugins being installed. This process may take a few minutes.

#### Creating the first administrator user <a id="creating-the-first-administrator-user"></a>

Finally, after [customizing Jenkins with plugins](https://jenkins.io/doc/book/installing/#customizing-jenkins-with-plugins), Jenkins asks you to create your first administrator user.

1. When the **Create First Admin User** page appears, specify the details for your administrator user in the respective fields and click **Save and Finish**.
2. When the **Jenkins is ready** page appears, click **Start using Jenkins**. **Notes:**
   * This page may indicate **Jenkins is almost ready!** instead and if so, click **Restart**.
   * If the page does not automatically refresh after a minute, use your web browser to refresh the page manually.
3. If required, log in to Jenkins with the credentials of the user you just created and you are ready to start using Jenkins!

|  | From this point on, the Jenkins UI is only accessible by providing valid username and password credentials. |
| :--- | :--- |


### Jenkins Parameters <a id="jenkins-parameters"></a>

Jenkins initialization can also be controlled by run time parameters passed as arguments. Command line arguments can adjust networking, security, monitoring, and other settings.

#### Networking parameters <a id="networking-parameters"></a>

Jenkins networking configuration is generally controlled by command line arguments. The networking configuration areguments are:

| Table 1. Jenkins Networking Command Line Parameters |  |
| :--- | :--- |
| Command Line Parameter | Description |
| `--httpPort=$HTTP_PORT` | Runs Jenkins listener on port $HTTP\_PORT using standard _http_ protocol. The default is port 8080. To disable \(because you’re using _https_\), use port `-1`. This option does not impact the root URL being generated within Jenkins logic \(UI, JNLP files, etc.\). It is defined by the Jenkins URL specified in the global configuration. |
| `--httpListenAddress=$HTTP_HOST` | Binds Jenkins to the IP address represented by $HTTP\_HOST. The default is 0.0.0.0 — i.e. listening on all available interfaces. For example, to only listen for requests from localhost, you could use: `--httpListenAddress=127.0.0.1` |
| `--httpsPort=$HTTPS_PORT` | Uses HTTPS protocol on port $HTTPS\_PORT. This option does not impact the root URL being generated within Jenkins logic \(UI, JNLP files, etc.\). It is defined by the Jenkins URL specified in the global configuration. |
| `--httpsListenAddress=$HTTPS_HOST` | Binds Jenkins to listen for HTTPS requests on the IP address represented by $HTTPS\_HOST. |
| `--http2Port=$HTTP_PORT` | Uses HTTP/2 protocol on port $HTTP\_PORT. This option does not impact the root URL being generated within Jenkins logic \(UI, JNLP files, etc.\). It is defined by the Jenkins URL specified in the global configuration. |
| `--http2ListenAddress=$HTTPS_HOST` | Binds Jenkins to listen for HTTP/2 requests on the IP address represented by $HTTPS\_HOST. |
| `--prefix=$PREFIX` | Runs Jenkins to include the $PREFIX at the end of the URL. For example, set _--prefix=/jenkins_ to make Jenkins accessible at _http://myServer:8080/jenkins_ |
| `--ajp13Port=$AJP_PORT` | Runs Jenkins listener on port $AJP\_PORT using standard _AJP13_ protocol. The default is port 8009. To disable \(because you’re using _https_\), use port `-1`. |
| `--ajp13ListenAddress=$AJP_ADDR` | Binds Jenkins to the IP address represented by $AJP\_HOST. The default is 0.0.0.0 — i.e. listening on all available interfaces. |
| `--sessionTimeout=$TIMEOUT` | Sets the http session timeout value to $SESSION\_TIMEOUT minutes. Default to what webapp specifies, and then to 60 minutes |

#### Miscellaneous parameters <a id="miscellaneous-parameters"></a>

Other Jenkins initialization configuration is also controlled by command line arguments. The miscellaneous configuration arguments are:

| Table 2. Jenkins Miscellaneous Command Line Parameters |  |
| :--- | :--- |
| Command Line Parameter | Description |
| `--argumentsRealm.passwd.$USER=$PASS` | Assigns the password for user $USER. If Jenkins security is enabled, you must log in as a user who has an _admin_role to configure Jenkins. |
| `--argumentsRealm.roles.$USER=admin` | Assigns user $USER the admin role. The user can configure Jenkins even if security is enabled in Jenkins. See [Securing Jenkins](https://jenkins.io/doc/book/system-administration/security/) for more information. |
| `--useJmx` | Enable [Jetty Java Management Extension \(JMX\)](https://www.eclipse.org/jetty/documentation/9.4.26.v20200117/jmx-chapter.html) |

Jenkins passes all command line parameters to the Winstone servlet container. More information about Jenkins Winstone command line parameters is available from the [Winstone Command Line Parameter Reference](https://github.com/jenkinsci/winstone#command-line-options).

|  | **Be Careful with Command Line Parameters** Jenkins ignores command line parameters it doesn’t understand instead of producing an error. Be careful when using command line parameters and make sure you have the correct spelling. For example, the parameter needed for defining the Jenkins administrative user is `--argument`**`s`**`Realm`and not `--argumentRealm`. |
| :--- | :--- |


#### Jenkins properties <a id="jenkins-properties"></a>

Some Jenkins behaviors are configured with Java properties. Java properties are set from the command line that started Jenkins. Property assignments use the form `-DsomeName=someValue` to assign the value `someValue` to the property named `someName`. For example, to assign the value `true` to a property `testName`, the command line argument would be `-DtestName=true`.

Refer to the detailed list of [Jenkins properties](https://wiki.jenkins.io/display/JENKINS/Features+controlled+by+system+properties#Featurescontrolledbysystemproperties-PropertiesinJenkinsCore) for more information.

### Configuring HTTP <a id="configuring-http"></a>

#### HTTPS with an existing certificate <a id="https-with-an-existing-certificate"></a>

If you’re setting up Jenkins using the built-in Winstone server and want to use an existing certificate for HTTPS:

```text
--httpPort=-1 \
--httpsPort=443 \
--httpsKeyStore=path/to/keystore \
--httpsKeyStorePassword=keystorePassword
```

The keystore should be in JKS format \(as created by the JDK 'keytool'\) and the keystore and target key must have the same password. \(Placing the keystore arguments after Jenkins-specific parameters does not seem to work; either they are not forwarded to Winstone or Winstone ignores them coming after unknown parameters. So, make sure they are adjacent to the working `--httpsPort` argument.\)

If your keystore contains multiple certificates \(e.g. you are using CA signed certificate\) Jenkins might end-up using a incorrect one. In this case you can [convert the keystore to PEM](http://stackoverflow.com/questions/7528944/convert-ca-signed-jks-keystore-to-pem) and use following command line options:

```text
--httpPort=-1 \
--httpsPort=443 \
--httpsCertificate=path/to/cert \
--httpsPrivateKey=path/to/privatekey
```

#### Using HTTP/2 <a id="using-http2"></a>

With Java 8 will not use HTTP/2 unless alpn boot jar is included in the bootclasspath. The alpn boot jar depends on your jvm version. Refer to the [Jetty documentation](https://www.eclipse.org/jetty/documentation/9.4.26.v20200117/alpn-chapter.html#alpn-versions) to select the required version.

You can download the required version from the [Apache maven repository](https://repo.maven.apache.org/maven2/org/mortbay/jetty/alpn/alpn-boot/).

Then you have to include it on jvm start:

```text
java -Xbootclasspath/p:alpn-boot-8.1.12.v20180117.jar \
    -jar target/jenkins.war \
    --http2Port=9090
```

#### HTTPS certificates with Windows <a id="https-certificates-with-windows"></a>

Creating a certificate for use within Jenkins. These instructions use a stock Jenkins installation on Windows Server. The instructions assume a certificate signed by a Certificate Authority such as Digicert. If making your own certificate skip steps 3, 4, and 5.

This process utilizes Java’s keytool. Use the Java `keytool` included with your Java installation.

**Step 1**: Create a new keystore on your server. This will place a 'keystore' file in your current directory.

```text
C:\>keytool -genkeypair -keysize 2048 -keyalg RSA -alias jenkins -keystore keystore
Enter keystore password:
Re-enter new password:
What is your first and last name?
[Unknown]: server.example.com
What is the name of your organizational unit?
[Unknown]: A Unit
What is the name of your organization?
[Unknown]: A Company
What is the name of your City or Locality?
[Unknown]: A City
What is the name of your State or Province?
[Unknown]: A State
What is the two-letter country code for this unit?
[Unknown]: US
Is CN=server.example.com, OU=A Unit, O=A Company, L=A City, ST=A State, C=US correct?
[no]: yes

Enter key password for <jenkins>
(RETURN if same as keystore password):
```

**Step 2**: Verify the keystore was created \(your fingerprint will vary\)

```text
C:\>keytool -list -keystore keystore
Enter keystore password:

Keystore type: JKS
Keystore provider: SUN

Your keystore contains 1 entry

jenkins, May 6, 2015, PrivateKeyEntry,
Certificate fingerprint (SHA1): AA:AA:AA:AA:AA:AA:AA:AA:AA:AA ...
```

**Step 3**: Create the certificate request. This will create a 'certreq.csr' file in your current directory.

```text
C:\>keytool -certreq -alias jenkins -keyalg RSA ^
-file certreq.csr ^
-ext SAN=dns:server-name,dns:server-name.your.company.com ^
-keystore keystore
Enter keystore password:
```

**Step 4**: Use the contents of the `certreq.csr` file to generate a certificate from your certificate provider. Request a SHA-1 certificate \(SHA-2 is untested but will likely work\). If using DigiCert, download the resulting certificate as Other format "a .p7b bundle of all the certs in a .p7b file".

**Step 5**: Add the resulting .p7b into the keystore you created above.

```text
C:\>keytool -import ^
-alias jenkins ^
-trustcacerts ^
-file response_from_digicert.p7b ^
-keystore keystore
Enter keystore password:
Certificate reply was installed in keystore
```

**Step 6**: Copy the 'keystore' file to your Jenkins secrets directory. On a stock installation, this will be at

```text
C:\Program Files (x86)\Jenkins\secrets
```

**Step 7**: Modify the &lt;arguments&gt; section of your `C:\Program Files (x86)\Jenkins\jenkins.xml` file to reflect the new certificate. Note: This example disables http via `--httpPort=-1` and places the server on `8443` via `--httpsPort=8443`.

```text
<arguments>
  -Xrs
  -Xmx256m
  -Dhudson.lifecycle=hudson.lifecycle.WindowsServiceLifecycle
  -jar "%BASE%\jenkins.war"
  --httpPort=-1
  --httpsPort=8443
  --httpsKeyStore="%BASE%\secrets\keystore"
  --httpsKeyStorePassword=your.password.here
</arguments>
```

**Step 8**: Restart the jenkins service to initialize the new configuration.

```text
net stop jenkins
net start jenkins
```

**Step 9**: After 30-60 seconds, Jenkins will have completed the startup process and you should be able to access the website at _https://server.example.com:8443_. Verify the certificate looks good via your browser’s tools. If the service terminates immediately, there’s an error somewhere in your configuration. Useful error information can be found in:

```text
C:\Program Files (x86)\Jenkins\jenkins.err.log
C:\Program Files (x86)\Jenkins\jenkins.out.log
```

