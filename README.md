# My Docker Environment

[boot2docker](https://github.com/steeve/boot2docker) is awesome I would
check that out instead if your just getting started.

I wanted something that I could leave running forever (and manage) with
vagrant (rather then virtualbox) since that is what I am
comfortable with.

Its important to node that you CAN use volumes (-v) from your OSX host
as long as your somewhere within $HOME since an NFS mount is created
between your home and the VM (this is amazing btw).

## Installation

Start by cloning this repo

```sh
git clone https://github.com/lightsofapollo/docker-env
cd docker-env
```

All below instructions assume a working directory inside docker-env

### Vagrant

follow instructions here: [vagrant](http://www.vagrantup.com/)

### Docker

Docker has both a server component and a client component. The server
component (where the container magic happens) will occur inside the
vagrant image. We want the client version.

Download the platform specific binary and place it on your PATH.

  - OSX: https://get.docker.io/builds/Darwin/x86_64/docker-latest 
  - LINUX: https://get.docker.io/builds/Linux/x86_64/docker-latest

For example on OSX:

```sh
curl https://get.docker.io/builds/Darwin/x86_64/docker-latest > /usr/local/bin/docker
```

Linux:

```sh
curl https://get.docker.io/builds/Linux/x86_64/docker-latest > /usr/local/bin/docker
```

### Start vagrant

```sh
# from the root
vagrant up
```

### Add the DOCKER_HOST to your environment variables

The `Vagrantfile` uses a private network configuration set to ip 192.168.50.10.
This means the `DOCKER_HOST` can be the same across installations and
you can easily each the docker host and containers within that host.


There is some manual configuration needed to get the benefits of this

```sh
# Add this environment variable somewhere (just ip:port no protocol)
DOCKER_HOST=192.168.50.10:4243
```

For example I added this to my .zshrc

```sh
#... stuff in zshrc
export DOCKER_HOST=192.168.50.10:4243
```

```sh
# reload zsh config
zsh
```

### Try it out

Run this:

```sh
docker ps
```

You should see something like this as a result:

```
CONTAINER ID        IMAGE                        COMMAND                CREATED             STATUS              PORTS                     NAMES
```

Additionally a host entry can be added if you do not want to remember
that ip address:

```
192.168.50.10 docker
```

### Usage

Follow the [docker docs](http://docs.docker.io/en/latest/)! Your all setup now
