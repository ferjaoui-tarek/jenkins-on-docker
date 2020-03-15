
```
# docker pull jenkins
```

```
# docker run -p 8080:8080 -p 50000:50000 jenkins
```

```
# docker run --name MyJenkins -p 8080:8080 -p 50000:50000 -v /Users/tarek/Desktop/Jenkins_Home:/var/jenkins_home jenkins

you can change the port by doing -p 8780:8080 for example
```

Her we change the port of for MyJnekins2 (9090)
```
# docker run --name MyJenkins2 -p 9090:8080 -p 50000:50000 -v /Users/tarek/Desktop/Jenkins_Home:/var/jenkins_home jenkins
```

We can create a volume 
```
# docker volume create myjenkins
```

List of all volumes
```
# docker volume ls
```

Inspect Volumes
```
# docker volume inspect myjenkins
```

```
# docker run --name MyJenkins3 -p 9090:8080 -p 50000:50000 -v myjenkins:/var/jenkins_home jenkins
```

```
# docker inspect MyJenkins3
```

In case you face issues like installing plugins on this Jenkins, can setup jenkins with this command:
```
# docker run -u root --rm -p 8080:8080 -v /srv/jenkins-data:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock   --name jenkins jenkinsci/blueocean
```
NOTES
Docker volume

By default all files created inside a container are stored on a writable container layer

The data doesn’t persist when that container is no longer running

A container’s writable layer is tightly coupled to the host machine where the container is running. You can’t easily move the data somewhere else.

Docker has two options for containers to store files in the host machine
so that the files are persisted even after the container stops

```VOLUMES```  and  ```BIND MOUNTS```

```Volumes``` are stored in a part of the host filesystem which is managed by Docker

Non-Docker processes should not modify this part of the filesystem

```Bind mounts``` may be stored anywhere on the host system

Non-Docker processes on the Docker host or a Docker container can modify them at any time

In Bind Mounts, the file or directory is referenced by its full path on the host machine. 


Volumes are the best way to persist data in Docker

volumes are managed by Docker and are isolated from the core functionality of the host machine

A given volume can be mounted into multiple containers simultaneously.

When no running container is using a volume, the volume is still available to Docker and is not removed automatically. You can remove unused volumes using docker volume prune.

When you mount a volume, it may be named or anonymous. 

Anonymous volumes are not given an explicit name when they are first mounted into a container

Volumes also support the use of volume drivers, which allow you to store your data on remote hosts or cloud providers, among other possibilities.
