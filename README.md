# Manual

<!-- # Badges -->

[![Github issues](https://img.shields.io/github/issues/2f0833e717/manual)](https://github.com/2f0833e717/manual/issues)
[![Github forks](https://img.shields.io/github/forks/2f0833e717/manual)](https://github.com/2f0833e717/manual/network/members)
[![Github stars](https://img.shields.io/github/stars/2f0833e717/manual)](https://github.com/2f0833e717/manual/stargazers)
[![Github top language](https://img.shields.io/github/languages/top/2f0833e717/manual)](https://github.com/2f0833e717/manual/)
[![Github license](https://img.shields.io/github/license/2f0833e717/manual)](https://github.com/2f0833e717/manual/)

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [WSL Manual](#wsl-manual)
  - [wsl install](#wsl-install)
  - [wsl uninstall](#wsl-uninstall)
  - [bash and dotfile settings](#bash-and-dotfile-settings)
  - [package install and update](#package-install-and-update)
    - [apt update](#apt-update)
    - [homebrew install](#homebrew-install)
    - [brew update](#brew-update)
- [Github Manual](#github-manual)
  - [github ssh connnection](#github-ssh-connnection)
  - [setting .gitconfig](#setting-gitconfig)
  - [github cli install](#github-cli-install)
  - [github get repositorys (api)](#github-get-repositorys-api)
  - [git commit message sample](#git-commit-message-sample)
- [Docker Manual](#docker-manual)
  - [Docker Install](#docker-install)
  - [Docker Uninstall](#docker-uninstall)
  - [docker-compose install](#docker-compose-install)
    - [python3 and pip install](#python3-and-pip-install)
- [npm Manual](#npm-manual)
  - [nvm install](#nvm-install)
  - [doctoc install](#doctoc-install)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# WSL Manual

## wsl install

> <https://docs.microsoft.com/ja-jp/windows/wsl/install-win10>

- Download on Microsoft Store
- Launch on Microsoft Store

Launch Ubuntu-20.04 Terminal

```bash
# UserName
ubuntu

# Password
ubuntu

exit
```

Windows Terminal

```bash
# settings default distro
wsl -s Ubuntu-20.04

# settings default distro view
wsl -l

# launch wsl
wsl
```

---

## wsl uninstall

- {Win-key} + i
- application
- serch `Ubuntu-20.04`
- uninstall

---

## bash and dotfile settings

```bash
mkdir -p ~/work
cd ~/work
git clone https://github.com/2f0833e717/dotfile
cd dotfile
cp -rf ./ ~/
cd
```

---

## package install and update

### apt update

> <https://qiita.com/SUZUKI_Masaya/items/1fd9489e631c78e5b007>

```bash
sudo apt update -y; \
sudo apt upgrade -y; \
sudo apt full-upgrade -y; \
sudo apt autoremove -y; \
sudo apt autoclean -y; \
sudo apt clean -y;
```

### homebrew install

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Next steps:
# - Add Homebrew to your PATH in /home/ubuntu/.profile:
################
# memo: not work /home/ubuntu/.profile
#       OK       /home/ubuntu/.bashrc
################
# echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/ubuntu/.bashrc # ~/.bashrc
# eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)" # one time setting
cat ~/.bashrc # check your ~/.bashrc

# reload wsl
# on wsl
exit
# on Windows Terminal
wsl
```

### brew update

```bash
brew update ; \
brew upgrade ; \
brew doctor ; \
# brew prune  # is old command @ Homebrew 1.9.0
brew cleanup ;
```

---

# Github Manual

## github ssh connnection

> <https://qiita.com/shizuma/items/2b2f873a0034839e47ce>

```bash
# generate ssh key
ssh-keygen -t rsa
# => {Enter x 3}

# Enter file in which to save the key (/home/ubuntu/.ssh/id_rsa):
# Created directory '/home/ubuntu/.ssh'.
# Enter passphrase (empty for no passphrase):
# Enter same passphrase again:
# Your identification has been saved in /home/ubuntu/.ssh/id_rsa
# Your public key has been saved in /home/ubuntu/.ssh/id_rsa.pub
# The key fingerprint is:
# SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx ubuntu@xxxxxxx-xxxxxxx
# The key's randomart image is:
# +---[RSA 3072]----+
# |=+.. .           |
# |o+= +..          |
# |.o.+o+=.         |
# |. ...*+o        +|
# |    .oE.S      +=|
# |    . o+..     ==|
# |     o .....  o.=|
# |      ... o.oo o.|
# |       oo  =+ .  |
# +----[SHA256]-----+

# Windows(wsl) only
clip.exe < ~/.ssh/id_rsa.pub
```

Move to

> <https://github.com/settings/keys>

- [New SSH Key]
- id_rsa
- Ctrl + V
- [Add SSH Key]

```bash
# vi ~/.ssh/config
Host github github.com
  HostName github.com
  IdentityFile ~/.ssh/id_rsa
  User git
```

```bash
# connection ssh
ssh -T github

# Are you sure you want to continue
# connecting (yes/no/[fingerprint])? yes
yes
```

---

## setting .gitconfig

```bash
# vi ~/.gitconfig
[url "github:"]
    InsteadOf = https://github.com/
    InsteadOf = git@github.com:
[user]
	name = 2f0833e717
	email = skinoshita202001082135@gmail.com
```

or

```bash
git config --global user.email "skinoshita202001082135@gmail.com"
git config --global user.name "2f0833e717"
```

---

## github cli install

install manual

> <https://github.com/cli/cli#macos>

```bash
# gh is homebrew only now...(linux install fail)
brew install gh
brew upgrade gh
# brew uninstall gh
brew list

gh auth login
# * Github.com
# * SSH
# * /home/ubuntu/.ssh/id_rsa.pub
# * Login with a web browser
# First copy your one-time code: XXXX-XXXX
# Enter => open browser
# Contrl + V
# [Authorize github]
# Login
# Enter => Logged in
```

get access-token

> <https://docs.github.com/ja/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token>

github cli manual

> <https://cli.github.com/manual/gh_pr_merge>

---

## github get repositorys (api)

```bash
# user-name:2f0833e717
curl -f -I -L https://api.github.com/users/2f0833e717/repos
```

or

```bash
# user-name:2f0833e717
curl -f -s -L https://api.github.com/users/2f0833e717/repos | \
grep "clone_url" | \
sed -e "s/\"clone_url\"\:\s\"//" | \
sed -e "s/\"\,$//"
```

---

## git commit message sample

```bash
git commit -m "{commit-message}"
```

feat: A new feature  
fix: A bug fix  
docs: Documentation only changes  
style: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)  
refactor: A code change that neither fixes a bug nor adds a feature  
perf: A code change that improves performance  
test: Adding missing or correcting existing tests  
chore: Changes to the build process or auxiliary tools and libraries such as documentation generation

> <https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#type>

---

# Docker Manual

## Docker Install

```bash
# instant docker install shell
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

# view docker version
docker -v
```

---

## Docker Uninstall

```bash
# docker uninstall
sudo apt-get purge docker-ce docker-ce-cli containerd.io -y
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```

---

## docker-compose install

### python3 and pip install

```bash
# python3 and pip install
sudo apt install python3 python3-pip -y

# pip setting
sudo pip3 install pip -U

# view pip version
pip -V
```

## Python仮想環境構築

```bash
sudo apt-get install python3-venv

python3 -m venv env-docker-compose

source env-docker-compose/bin/activate

```

## pipバグアップデート

```bash
pip install --upgrade pip setuptools
```

## docker-compose install

```bash
# docker-compose install
pip install docker-compose

# view docker-compose version
docker-compose -v
```

## Pythonのバージョン間の差異を解決するsixをインストール

```bash
sudo -H pip install -I six
sudo pip uninstall docker-compose
sudo pip install -I docker-compose
```

---

# npm Manual

## nvm install

```bash
git clone https://github.com/creationix/nvm.git ~/.nvm
source ~/.nvm/nvm.sh

# install node lts version
nvm install --lts

# view nvm version
nvm -v
```

```bash
# ~/.bashrc
if [ -s ~/.nvm/nvm.sh ]; then
  source ~/.nvm/nvm.sh
fi
```

---

## doctoc install

> <https://github.com/thlorenz/doctoc>

```bash
# sudo npm install -g doctoc # ?
npm install -g doctoc

# on root project folder
# cd {project-folder}
mkdir -p .github/workflows
touch .github/workflows/toc.yml
```

doctoc setting

```bash
# vi .github/workflows/toc.yml
on: push
name: TOC Generator
jobs:
  generateTOC:
    name: TOC Generator
    runs-on: ubuntu-latest
    steps:
      - uses: technote-space/toc-generator@v4
```

doctoc use

```bash
doctoc .
```
