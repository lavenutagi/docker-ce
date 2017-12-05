# Setup Docker CE on RHEL 7 / CentOS 7

### Reference guide:

* [Get Docker CE for CentOS]

### Preconditions:

* RHEL 7 or CentOS 7 on bare metal or VM

## Step 1: Setup the repository

```sh
$ sudo yum install -y yum-utils device-mapper-persistent-data lvm2

$ sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

## Step 2: Install Docker CE

```sh
$ sudo yum install docker-ce
```

## Step 3: Start Docker CE

```sh
$ sudo systemctl start docker
```

## Step 4: Configure Docker to start on boot

```sh
$ sudo systemctl enable docker
```

## Step 5: Add user to the docker group

```sh
$ sudo groupadd docker

$ sudo usermod -aG docker $USER
```

## Step 6: Install Docker Compose (optional)

> Check for new releases at https://github.com/docker/compose/releases/

```sh
$ cd ~

$ curl -L https://github.com/docker/compose/releases/download/1.17.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```

Apply executable permissions to the binary:

```sh
$ sudo chmod +x /usr/local/bin/docker-compose
```

[Get Docker CE for CentOS]: <https://docs.docker.com/engine/installation/linux/docker-ce/centos/>