---
layout: post
title: Docker Notes
tags: Automation
category: Tech
---

### Concepts 

#### Container Architecture vs Hypervisor Architecture 

<img class="img-responsive" alt="Docker vs VM Architecture" src="{{ site.url }}/assets/images/Docker-Compared-To-Vms.png"/>

#### Open Source on GitHub 

- Apache License 2.0  
- Multiple tools in the project  
- Core components are written in Go or Golang  

[View Docker Repos](https://github.com/docker)  

#### Ops needed for containers

There are various tools that ops needs for managing containers in production including:  

- Orchestration tools  
- Clustering tools  
- Management tools  
- Monitoring & logging tools  

### In Practice 

#### Common Commands

~~~
docker ps
docker stop
docker image ls
docker exec -it <instance name> /bin/bash
docker stop <instance name>
docker container run -p 9999:80 --name <instance name> nginx:latest
docker run --name <instance name> -v <local path>:<docker image path>  -p <local port>:<docker image port> --rm nginx:latest
~~~

#### Dockerfile

~~~
FROM nginx:latest
EXPOSE 80
RUN apt-get update && apt-get -y install vim
LABEL maintainer="markpearl@gmail.com"
VOLUME /Users/mark.pearl/Source/personal/tmp3/nginx/:/usr/share/nginx/html 
~~~

#### References 

[Docker Hub](https://hub.docker.com)  
[Docker & Containers: The Big Picture](https://app.pluralsight.com/library/courses/docker-containers-big-picture)  
[Working with container basics](https://www.simple-talk.com/sysadmin/virtualization/working-windows-containers-docker-basics/)  
