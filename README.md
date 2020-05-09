# mac-dev-setup
My datascience and development setup for macOS

I took lots of inspiration from 
[nicolashery/mac-dev-setup](https://github.com/nicolashery/mac-dev-setup)

# Setup

Clone this repository
```bash
mkdir ~/src
cd src
git clone https://github.com/elijahc/mac-dev-setup
```

# Homebrew

Install homebrew
```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Install homebrew applications
```bash
cd ~/src/mac-dev-setup  && ./brew.sh
```

# Terminal Configuration

## ZSH
Install Oh My Zsh
```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Install zsh-syntax-highlighting
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

## Git

`brew.sh` should have installed git for you, now it just needs to be configured

```bash
touch ~/.gitconfig
```

Update gitconfig
```ini
[user]
  name   = Firstname Lastname
  email  = you@example.com
[github]
  user   = username
[alias]
  a      = add
  cm     = commit -m
  s      = status
```

## SSH
```bash
mkdir ~/.ssh && touch ~/.ssh/config
```

update `.ssh/config`
```ini
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa

Host myssh
  HostName example.com
  User user
  IdentityFile ~/.ssh/key.pem
```

## Vim

Use Tim Pope's sensible vim defaults

```bash
mkdir -p ~/.vim/pack/tpope/start
cd ~/.vim/pack/tpope/start
git clone https://tpope.io/vim/sensible.git
```

## Dotfiles configuration
I keep all of my application specifc configs in 
[elijahc/dotfiles](https://github.com/elijahc/dotfiles)

Clone dotfiles repo into `~/.dotfiles`
```bash
git clone https://github.com/elijahc/dotfiles .dotfiles
```

# Programming Languages

## Ruby

Install rbenv
```bash
brew install rbenv
```

Add the following to `.bash_profile`/`.bashrc`:
```bash
eval "$(rbenv init -)"
```

## Python

macOS, like Linux, ships with Python already installed. I like using `pyenv` to manage multiple versions of Python (ex: 2.7 and 3) should we need to.


Install pyenv via Homebrew by running:
```bash
brew install pyenv pyenv-virtualenv
```

Add the following to `.bash_profile`/`.bashrc`:
```bash
# Load pyenv and virtual env
if command -v pyenv 1>/dev/null 2>&1; then eval "$(pyenv init -)"; fi
if which pyenv-virtualenv-init > /dev/null; then eval "$(pyenv virtualenv-init -)"; fi
```
