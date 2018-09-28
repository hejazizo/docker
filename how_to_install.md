# Installing docker on Linux

Quick and easy way of installing using apt:

`$ sudo apt install docker.io`

Problem:
- You get an old version (at least a year old)

To get the latest version, install through store:
store.docker.com
and follow the steps. Very detailed walkthrough.

How to cheat this and have the latest docker version installed in a quick way:<br />
go to:
- get.docker.com
A script used with curl that will allow an automated install:
<br/> it works very well for local installs <br/>
`$ curl -fsSL get.docker.com -o get-docker.sh`<br/>
`$ get-docker.sh`

# Adding docker account to the docker group [optional]
This will allow working with docker commands without the need of sudo. But if you're concerned about security you don't need to do this part. and that's because docker needs root access in order to do what it needs to do with the core functionality of linux. So by adding your user to the docker user group, what you're effectively doing is giving that user the ability to run a docker container layer that could then have root permisions on the host. If this just your local machine than you dont have to worry about this too much.
If you're not adding your user, then you will need to run the commands with sudo.

`$ sudo usermod -aG docker yourname`

log out and back in

Install two other tools:
- docker machine
- docker compose

# Installing Docker Machine
Install from: https://docs.docker.com/machine/install-machine/
<br/>Copy and paste in terminal:
```
$ base=https://github.com/docker/machine/releases/download/v0.14.0 &&
  curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine &&
  sudo install /tmp/docker-machine /usr/local/bin/docker-machine
```
to check install and latest verion:<br/>
`$ docker-machine --version`

To check for latest version, you can visit:
github.com/machine/releases
<br/> check for the latest release

# Installing Docker Compose
Install from: https://docs.docker.com/compose/install/

<br/>Copy and paste in terminal:
```
$ base=https://github.com/docker/machine/releases/download/v0.14.0 &&
  curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine &&
  sudo install /tmp/docker-machine /usr/local/bin/docker-machine
```

To check for latest version, you can visit:
github.com/compose/releases
<br/> check for the latest release

NOTE: Because we have manually installed docker compose, we would need to manually check for updates. So have this on your mental check list every month or two, because they do update quickly.
