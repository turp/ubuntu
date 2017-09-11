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

