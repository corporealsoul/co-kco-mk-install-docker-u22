## Install Docker Engine on Ubuntu,

https://docs.docker.com/engine/install/ubuntu/


### Run the following command to uninstall all conflicting packages,

    anup@ubuntu-22042-08:~$ docker version
    
    anup@ubuntu-22042-08:~$ for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

### Install using the apt repository,

**Set up the repository,**

    anup@ubuntu-22042-08:~$ sudo apt-get update
    
    anup@ubuntu-22042-08:~$ sudo apt-get install ca-certificates curl GnuPG

<br>

    anup@ubuntu-22042-08:~$ sudo install -m 0755 -d /etc/apt/keyrings
    
    anup@ubuntu-22042-08:~$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    
    anup@ubuntu-22042-08:~$ sudo chmod a+r /etc/apt/keyrings/docker.gpg

<br>

    anup@ubuntu-22042-08:~$ echo \
      "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
      "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
      sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

**Install Docker Engine,**

    anup@ubuntu-22042-08:~$ sudo apt-get update
    
    anup@ubuntu-22042-08:~$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

<br>

    anup@ubuntu-22042-08:~$ docker --version
    
    anup@ubuntu-22042-08:~$ sudo systemctl status docker.service 
    
    anup@ubuntu-22042-08:~$ sudo systemctl enable docker.service 
    
    anup@ubuntu-22042-08:~$ sudo docker run hello-world


### Manage Docker as a non-root user,

    anup@ubuntu-22042-08:~$ sudo groupadd docker
    
    anup@ubuntu-22042-08:~$ sudo usermod -aG docker $USER
    
    anup@ubuntu-22042-08:~$ newgrp docker
    
    anup@ubuntu-22042-08:~$ docker run hello-world
