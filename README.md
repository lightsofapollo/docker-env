# My Docker Environment

[boot2docker](https://github.com/steeve/boot2docker) is awesome I would
check that out instead if your just getting started.

I wanted something that I could leave running forever (and manage) with
vagrant (rather then virtualbox) since that is what I am
comfortable with.


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

DOCKER_HOST is a magic environment variable recognized by the docker
CLI. If your docker server is running on the same machine as your host
you don't need to care about this but in our case we need to tell the
client where to connect:

```sh
# Add this environment variable somewhere (just ip:port no protocol)
DOCKER_HOST=127.0.0.1:4243
```

For example I added this to my .zshrc

```sh
#... stuff in zshrc
export DOCKER_HOST=127.0.0.1:4243
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

### Usage

Follow the [docker docs](http://docs.docker.io/en/latest/)! Your all setup now
