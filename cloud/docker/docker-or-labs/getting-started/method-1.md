# Method 1

## Run container with:

```text
docker run -it -v /var/run/dockersock:/var/run/docker.sock &&
-v jenkins-data:/var/jenkins_home -p 8080:8080 getintodevops/jenkins-withdocker:lts-docker18.06.0
```

`-it` interactive tty : we want to have an interactive terminal within the container once it's started.

`-v /var/run/docker.sock:/var/run/docker.sock` is where the socket usually resides. we mount the docker socket using the valume using the -v argument

`-v jenkins-data:/var/jenkins_home` assign/attach the jenkins home directory. This way when we restart this container we don't have to reinstall everything.

