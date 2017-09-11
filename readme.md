# Ubuntu setup

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

