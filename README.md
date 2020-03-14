
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