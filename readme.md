# Ubuntu setup

## Basics

* Chrome
* VS Code

## Docker

Source: https://docs.docker.com/install/linux/docker-ce/ubuntu

### Uninstall old versions

Older versions of Docker were called docker or docker-engine. If these are installed, uninstall them:

```
sudo apt-get remove docker docker-engine docker.io
```

Update the apt package index:

```
sudo apt-get update
```

Install packages to allow apt to use a repository over HTTPS:

```
sudo apt-get install \
  apt-transport-https \
  ca-certificates \
  curl \
  software-properties-common
```

Add Docker’s official GPG key:

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Verify that you now have the key with the fingerprint 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88, by searching for the last 8 characters of the fingerprint.

```
sudo apt-key fingerprint 0EBFCD88

pub   4096R/0EBFCD88 2017-02-22
      Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid                  Docker Release (CE deb) <docker@docker.com>
sub   4096R/F273FCD8 2017-02-22
```
Use the following command to set up the stable repository. 

```
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   artful stable"
```

Update the apt package index.

```
sudo apt-get update
```

Verify that everything in configured properly

```
$ apt-cache search docker-ce

docker-ce - Docker: the open-source application container engine
```

Install the latest version of Docker CE, or go to the next step to install a specific version:

```
sudo apt-get install docker-ce
```

Verify that Docker CE is installed correctly by running the hello-world image.

```
sudo docker run hello-world
```

If you don’t want to use sudo when you use the docker command, create a Unix group called docker and add users to it. When the docker daemon starts, it makes the ownership of the Unix socket read/writable by the docker group.

```
sudo groupadd docker
sudo usermod -G docker -a $USER
```

Restart machine so that your group membership is re-evaluated.

Verify that you can run docker commands without sudo.

```
docker run hello-world
```

## Erlang

https://hexdocs.pm/phoenix/installation.html

```
wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb && sudo dpkg -i erlang-solutions_1.0_all.deb
sudo apt-get update
sudo apt-get install esl-erlang

sudo apt-get install elixir
mix local.hex
mix archive.install https://github.com/phoenixframework/archives/raw/master/phx_new.ez

curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs

sudo apt-get install postgresql postgresql-contrib
sudo apt-get install postgresql-client
sudo apt-get install pgadmin3
```

## Basic Postgress Server Setup

To start off, we need to set the password of the PostgreSQL user (role) called "postgres"; we will not be able to access the server externally otherwise. As the local “postgres” Linux user, we are allowed to connect and manipulate the server using the psql command.

In a terminal, type:

```
sudo -u postgres psql postgres
```

this connects as a role with same name as the local user, i.e. "postgres", to the database called "postgres" (1st argument to psql).

Set a password for the "postgres" database role using the command:

```
\password postgres
```

and give your password when prompted. **Phoenix assumes password will be 'postgres'.** The password text will be hidden from the console for security purposes.

Type Control+D or \q to exit the posgreSQL prompt. 


```
sudo apt-get install vim

sudo apt-get install inotify-tools

```
# Hello world

```
mix phx.new hello
```
We are all set! Go into your application by running:

```
cd hello
```

Then configure your database in config/dev.exs and run:

```
mix ecto.create
```

Start your Phoenix app with:

```
mix phx.server
```

You can also run your app inside IEx (Interactive Elixir) as:

    $ iex -S mix phx.server

