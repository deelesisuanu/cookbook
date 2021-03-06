---
title: Install Docker on Ubuntu
image: docker-ubuntu.png
---

<span class="w3-tag w3-green">ubuntu 16.04, 64-bit</span> 

## Step 1: Install Docker Engine

```sh
sudo apt-get -y install apt-transport-https
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) \
    stable"
sudo apt-get update
sudo apt-get install -y docker-ce
sudo usermod -aG docker $USER # Add current user to the "docker" group
```

## Step 2: Install Docker Compose

```sh
VERSION=1.20.1
sudo curl -L https://github.com/docker/compose/releases/download/${VERSION}/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

## Step 3: Verify installation

```sh
docker run hello-world
docker-compose version
```