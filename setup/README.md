# Setup Docker

Docker runs as a background service on server operating systems, but in a local environment the easiest option is Docker Desktop.

## Git Client - Mac, Windows or Linux

Git is a free, open source tool for source control:

- [Install Git](https://git-scm.com/downloads)

## Docker Desktop - Mac or Windows

If you're on macOS or Windows 10, Docker Desktop is for you:

- [Install Docker Desktop](https://www.docker.com/products/docker-desktop)

The download and install takes a few minutes. When it's done, run the _Docker_ app and you'll see the Docker whale logo in your taskbar (Windows) or menu bar (macOS).

> On Windows 10 the install may need a restart before you get here.

> If you're using WSL on Windows 10, it's much easier to use Docker Desktop which integrates with your WSL distro.

## Docker Engine - Linux

Recently [Docker Desktop is also released for Linux](https://docs.docker.com/desktop/install/linux-install/)

Docker Engine is the background service which runs containers. You can install it - along with the Docker command line - for lots of different Linux distros:

 - [Install Docker Engine](https://docs.docker.com/engine/install/)
 - [Install Docker Compose](https://docs.docker.com/compose/install/)

## Check your setup

When you have Git and Docker installed you should be able to run these commands and get some output:

```shell
git --version
```

I'm using Git for Linux and my output is:

```
git version 2.35.4
```

Then run:

```
docker version
```

I'm using Docker on Linux and mine says:

```
Client: Docker Engine - Community                                                                                      
 Version:           20.10.18                                                                                           
 API version:       1.41                                                                                               
 Go version:        go1.19.1                                                                                           
 Git commit:        e42327a6d3c55ceda3bd5475be7aae6036d02db3                                                           
 Built:             Mon Sep 12 19:08:00 2022                             
 OS/Arch:           linux/amd64                                          
 Context:           default                                                                                            
 Experimental:      true                                   
                                                           
Server: Docker Engine - Community                                        
 Engine:                
  Version:          20.10.18        
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.19.1
  Git commit:       e42327a6d3c55ceda3bd5475be7aae6036d02db3                                                                                      
  Built:            Mon Sep 12 19:07:26 2022   
  OS/Arch:          linux/amd64                                          
  Experimental:     false                                                                                              
 containerd:                                               
  Version:          v1.6.8                                 
  GitCommit:        9cd3357b7fd7218e4aec3eae239db1f68a5a6ec6                                                                                      
 runc:      
  Version:          1.1.4 
  GitCommit:        5fd4c4d144137e991c4acebb2146ab1483a97925
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
```

And then:

```
docker-compose version
```

My output is:

```
Docker Compose version v2.10.2
```

> Your details and version numbers may be different - that's fine. If you get errors then we need to look into it, because you'll need to have Docker running for all of the exercises.

> ❗ If you're running Docker Desktop on Windows, make sure you're in _Linux container mode_. This is the default mode, but if you've changed to using Windows containers (from the whale toolbar menu), then you'll need to switch back.

<br>

# Running a Local Kubernetes Cluster

Kubernetes clusters can have hundreds of nodes in production, but you can run a single-node cluster on your laptop and it works in the same way.

## Docker Desktop - Mac or Windows

If you're on macOS or Windows 10 Docker Desktop is the easiest way to get Kubernetes:

Right-click that whale and click _Settings_:

![](/imgs/docker-desktop-settings.png)

In the settings Windows select _Kubernetes_ from the left menu and click _Enable Kubernetes_: 

![](/imgs/docker-desktop-kubernetes.png)

> Docker downloads all the Kubernetes components and sets them up. That can take a few minutes too. When the Docker logo and the Kubernetes logo in the UI are both green, everything is running.

## minikube - Linux

`minikube` is a tool that lets you run Kubernetes locally. minikube runs a single-node Kubernetes cluster on your personal computer (including Windows, macOS and Linux PCs) so that you can try out Kubernetes, or for daily development work.

You can follow the official [Get Started!](https://minikube.sigs.k8s.io/docs/start/) guide to get the tool installed.

Once you have minikube working, you can use it to [run a sample application](https://kubernetes.io/docs/tutorials/hello-minikube/).

## Kubectl

The Kubernetes command-line tool, `kubectl`, allows you to run commands against Kubernetes clusters. You can use `kubectl` to deploy applications, inspect and manage cluster resources, and view logs.

kubectl is installable on a variety of Linux platforms, macOS and Windows. Find your preferred operating system below.

- [Install kubectl on Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux)
- [Install kubectl on macOS](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos)
- [Install kubectl on Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows)

## Check your Kubernetes cluster

Whichever setup you use, you should be able to run this command and get some output about your cluster:

```
kubectl get nodes
```

I'm using Docker Desktop and mine says:

```
NAME       STATUS   ROLES                  AGE    VERSION
minikube   Ready    control-plane,master   257d   v1.22.2
```

> Your details may be different - that's fine. If you get errors then we need to look into it, because you'll need your own cluster for every part of the course.