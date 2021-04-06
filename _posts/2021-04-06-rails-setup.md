---
layout: post
title: rails set·up
---

Right now, almost half of my career was spent writing PHP code in Laravel. It was my first encounter with the MVC world, I fell in love immediately and it was easy to build products with it. The joy of putting up a quick project within minutes by the use of artisan commands and rapid scaffolding generation was definitely hard to reject as a developer. Then, I met Ruby and the mature yet reliable Rails. I discovered that the _Build a blog in 15 minutes_ wasn't a well-known thing until [DHH](https://twitter.com/dhh) [demonstrated](https://youtu.be/Gzj723LkRJY) how possible it is using a newly introduced web framework back in 2005. In this post, I'm going to share how a developer can spin up a fresh Ruby on Rails project with [asdf](https://github.com/asdf-vm/asdf) in 2021.

In this setup guide, I'm working with a _WSL2 + Ubuntu 20.04_ environment so it might be different to yours. If you're on a UNIX-based system, that shouldn't stop you from following through. In addition, you might want to swap out that SQLite with a fresh PostgreSQL install (I'm not going to teach this now but you can search for a bunch of articles online that will help you out depending on your machine). Now, let's get started!

Let's install _asdf_ on our machine. We need `git` as it is a dependency before you can get _asdf_ so make sure you have that as well. Also, _asdf_ has a pretty straightforward [documentation](https://asdf-vm.com/#/core-manage-asdf) so definitely check it out if you can.

First, let's clone the latest branch:

```shell
  git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.8.0
```

Then let's add it to our shell.

If you're on _Bash_ or _ZSH_, add the following to your `~/.bashrc` or `~/.zshrc`:

```shell
  . $HOME/.asdf/asdf.sh
```

If you're a _Fish_ user, add this to your `~/.config/fish/config.fish` instead:

```shell
  source ~/.asdf/asdf.fish
```

We have to do some manual configuration of our settings for the completion feature. For _Bash_, add the following on your `~/.bashrc`:

```shell
  . $HOME/.asdf/completions/asdf.bash
```

On _ZSH_, add these to your `~/.zshrc`:

```shell
  # append completions to fpath
  fpath=(${ASDF_DIR}/completions $fpath)
  # initialise completions with ZSH's compinit
  autoload -Uz compinit
  compinit
```

For _Fish_, run the following command on your console:

```shell
  mkdir -p ~/.config/fish/completions; and ln -s ~/.asdf/completions/asdf.fish ~/.config/fish/completions
```

Done! That should be enough to get `asdf` installed on your machine. If you're having issues, check [this](https://asdf-vm.com/#/core-manage-asdf?id=having-issues).

Now let's go to the next step which is to install the necessary plugins to create our Rails project.

Of course, there's no Rails without Ruby so let's start with that first. In _asdf_, they call packages as _plugins_. So whenever I mention the term _plugin_ in this section, I mean packages. 😉

Let's add our first _asdf_ plugin via the `add` command:

```shell
  asdf plugin add ruby
```

Then let's install the latest version of Ruby via `install`:

```shell
  asdf install ruby latest
```

Afterwards, let's set our machine's global Ruby version via:

```shell
  asdf global ruby <version>
  # asdf global ruby 2.7.1
```

To check installed versions, just run:

```shell
  asdf list ruby
```

Now that we have Ruby, we also need to take care of the front-end side of things since Rails also uses _webpacker_ so let's install both _nodejs_ and _yarn_ to manage our packages.

```shell
  asdf plugin add nodejs && asdf plugin add yarn
```

Then, proceed to add versions like how we installed Ruby earlier.

```shell
  asdf install nodejs latest && asdf install yarn latest
```

To check if we successfully installed the plugins, use the general command:

```shell
  asdf list
```

Nice, we're ready to install Rails now so let's do just that:

```shell
  gem install rails
```

Then let's proceed and create our new project with PostgreSQL as our database:

```shell
  rails new project-name -d postgresql
```

There we go! Now we have a new Rails project using _asdf_ with _PostgreSQL_ as the substitute database to SQLite. To test the local server, just run this within the project folder:

```shell
  rails server
  # or rails s
```

This should spin up your local server and now you'll be able to check your fresh Rails app on the browser via `http://localhost:3000/`.

That's it for this setup guide, I hope this is useful to you as it is to me. If you need additional assistance, ping me at nardparagas@gmail.com or on Twitter via @nards_paragas. I'd be happy to help out. Thanks for reading this guide!

<hr/>

Further Notes:

If the project shows an error on the browser saying that you're failing to connect to the database port, don't forget to start PostgreSQL via:

```shell
  sudo service postgresql start
```

Then if the project displays an error telling you that `project-name_development` database doesn't exist then run the following on your console with the project being the root:

```shell
  bundle install
  # To ensure that all required dependencies are already installed

  rails db:create
  rails db:migrate
  # To create a new local database named after your project with the _development and _test name extensions

  rails server
  # Or rails s to run your local server
```
