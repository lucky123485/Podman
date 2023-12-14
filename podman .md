![](https://lh7-us.googleusercontent.com/NXF1lcSjd9AiM_Uh9RFp0t3t-bGCF5sxJEyoXBpaXEqnoD9Rn25cgxeO0Q4hmsDXnXfuGvqKrSLabwAeFlZq40_nxs6E2YiRYQdBisJ8X30dCxxSZPDqYZ9mXUqH8Xz6C8qSQtpVLRESD7JHyajo1t0)
# Table of content

[What is Podman?](#WhatisPodman?)

[Why Podman? (Features of Podman)](#WhyPodman? (Features of Podman))

[What are Pods?](#WhatarePods)

[Buildah and Skopea](#BuildahandSkopea)

[Containers](#Containers)

[Step for Installation](#StepforInstallation)

# What is Podman?<a id="what-is-podman"></a>

- Podman provides a secure and lightweight alternative to docker for creating and managing containers on Linux systems.

- Podman allows you to package an application and its dependencies into a single container that can run anywhere without any dependency on the host system.


# Why Podman? (Features of Podman)<a id="why-podman-features-of-podman"></a>

- Daemonless:- Podman does not require background daemon to run, make it more lightweight and efficient than Docker.

* Rootless Containers:- To run PODMAN containers, root privileges are not required.

- Multi-Container Application:- Podman supports running multiple containers as part of an application, and it provides tools for managing and connecting these containers.

* More Secure:- Podman launches each container with a security enhanced linux(SELinux) label and its rootless feature makes it more secure.


# What are Pods?<a id="what-are-pods"></a>

Pods are a group of containers that run together and share the same resources.

# Buildah and Skopea

Both used with Podman to manager container images and build container.

* Buildah:- Used to create container images.

* Skopea:- Used to push and pull images from remote registries.

# Containers<a id="containers"></a>

A container is a lightweight, portable, and self-sufficient unit that can run applications and their dependencies. Containers package the application code, runtime, libraries, and other necessary components into a single unit. They run on a shared operating system kernel and isolate the application processes from each other and from the host system. Popular containerization platforms include Docker and container orchestration tools like Kubernetes.


# Step for Installation:-<a id="step-for-installation-"></a>

## Prerequisite<a id="prerequisite"></a>
```
lsb\_release -a
```

No LSB modules are available.

Distributor ID: Ubuntu

Description: Ubuntu 22.04.3 LTS

Release: 22.04


```
sudo apt update
```

```
sudo apt-get install podman
```

```
podman info
```

```
podman version
```

Version:      4.6.2

API Version:  4.6.2

Go Version:   go1.18.1

Built:        TThu Jan  1 05:30:00 1970

OS/Arch:      linux/amd64
 
 # Creating Alias

 alias docker=podman

# To Search for a image in registry<a id="to-search-for-a-image-in-registry"></a>
```
Podman search nginx
```


# Checking already downloaded images

Podman images

REPOSITORY                    TAG         IMAGE ID      CREATED       SIZE
docker.io/library/nginx       latest      a6bd71f48f68  2 weeks ago   191 MB
docker.io/jasonrivers/nagios  latest      653834b48d9f  2 months ago  831 MB


# To download an image


podman pull docker.io/library/nginx

Trying to pull docker.io/library/nginx:latest...
Getting image source signatures
Copying blob 84b1ff10387b skipped: already exists  
Copying blob c6edf33e2524 skipped: already exists  
Copying blob 9ea27b074f71 skipped: already exists  
Copying blob 9b16c94bb686 skipped: already exists  
Copying blob 9a59d19f9c5b skipped: already exists  
Copying blob 517357831967 skipped: already exists  
Copying blob 1f7ce2fa46ab skipped: already exists  
Copying config a6bd71f48f done  
Writing manifest to image destination
a6bd71f48f6839d9faae1f29d3babef831e76bc213107682c5cc80f0cbb308

# To run an image<a id="to-run-an-image"></a>

```
podman run docker.io/library/ngnix
```

/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2023/12/13 05:12:49 [notice] 1#1: using the "epoll" event method
2023/12/13 05:12:49 [notice] 1#1: nginx/1.25.3
2023/12/13 05:12:49 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14) 
2023/12/13 05:12:49 [notice] 1#1: OS: Linux 6.2.0-26-generic
2023/12/13 05:12:49 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2023/12/13 05:12:49 [notice] 1#1: start worker processes
2023/12/13 05:12:49 [notice] 1#1: start worker process 24
2023/12/13 05:12:49 [notice] 1#1: start worker process 25
2023/12/13 05:12:49 [notice] 1#1: start worker process 26
2023/12/13 05:12:49 [notice] 1#1: start worker process 27
2023/12/13 05:12:49 [notice] 1#1: start worker process 28
2023/12/13 05:12:49 [notice] 1#1: start worker process 29
2023/12/13 05:12:49 [notice] 1#1: start worker process 30
2023/12/13 05:12:49 [notice] 1#1: start worker process 31



# To run an image in a background <a id="to-run-an-image-in-a-background"></a>

```
podman run -d docker.io/library/ngnix
```

5532a5af1e5cc4d883ab31c696c85956cb15c10e2440e726cb11fe10afd8211c



# To see the running containers<a id="to-see-the-running-containers"></a>

```
Podman ps
```

CONTAINER ID  IMAGE                           COMMAND               CREATED             STATUS             PORTS       NAMES
5532a5af1e5c  docker.io/library/nginx:latest  nginx -g daemon o...  About a minute ago  Up About a minute              ecstatic_dirac



bhavesh@bhavesh-HP-Laptop-15-da1xxx:~$ ifconfig
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:5c:1b:51:ae  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 9c:7b:ef:20:16:31  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 7456  bytes 705807 (705.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7456  bytes 705807 (705.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.20  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::350a:2a1d:2947:2d73  prefixlen 64  scopeid 0x20<link>
        inet6 2401:4900:1c23:58e3:5697:77cc:7391:4220  prefixlen 64  scopeid 0x0<global>
        inet6 2401:4900:1c23:58e3:240e:7a7c:9f5a:31f8  prefixlen 64  scopeid 0x0<global>
        ether dc:f5:05:ed:5a:7f  txqueuelen 1000  (Ethernet)
        RX packets 33459  bytes 15698340 (15.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 22949  bytes 9142890 (9.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


![Alt text](<Screenshot from 2023-12-13 12-12-58.png>)

# Port Binding of container<a id="port-binding-of-container"></a>

```
podman run -dt -p 8080:80/tcp docker.io/library/nginx
```

96ad8fd7b38ae65d9bcb456e03e74bb8b094eedb666e39a68ce6e9f3e70a58f6

bhavesh@bhavesh-HP-Laptop-15-da1xxx:~$ docker ps

CONTAINER ID   IMAGE                           COMMAND               CREATED         STATUS         PORTS                    NAMES
5532a5af1e5c  docker.io/library/nginx:latest  nginx -g daemon o...  55 minutes ago  Up 55 minutes                           ecstatic_dirac
96ad8fd7b38a  docker.io/library/nginx:latest  nginx -g daemon o...  37 seconds ago  Up 37 seconds  0.0.0.0:34873->8080/tcp  xenodochial_wozniak



!![Alt text](<Screenshot from 2023-12-13 12-14-07.png>)


# To Stop a container<a id="to-stop-a-container"></a>

```
podman stop \<container\_name / container id>
```

```
bhavesh@bhavesh-HP-Laptop-15-da1xxx:~$ podman stop 5532a5af1e5c

5532a5af1e5c
---

---

# To run multiple containers with different port<a id="to-run-multiple-containers-with-different-port"></a>

```
podman run -dt -p 8081:80/tcp docker.io/library/nginx

podman run -dt -p 8082:80/tcp docker.io/library/nginx
```


# To see all the existing containers<a id="to-see-all-the-existing-containers"></a>

```
Podman ps -a
```

# To remove the existing containers<a id="to-remove-the-existing-containers"></a>

podman rm \<container\_name>
