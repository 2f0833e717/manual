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
  - [Windows Terminal Install](#windows-terminal-install)
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
  - [github commit rebase/autoSquash](#github-commit-rebaseautosquash)
  - [git commit message sample](#git-commit-message-sample)
- [Docker Manual](#docker-manual)
  - [Docker Install](#docker-install)
  - [Docker Uninstall](#docker-uninstall)
  - [docker-compose install](#docker-compose-install)
    - [python3 and pip install](#python3-and-pip-install)
  - [Python venv](#python-venv)
  - [Python virtualenv](#python-virtualenv)
  - [pip bug update](#pip-bug-update)
  - [docker-compose install](#docker-compose-install-1)
  - [Python fix library version](#python-fix-library-version)
- [Language setup](#language-setup)
  - [Golang setup](#golang-setup)
  - [Java setup](#java-setup)
- [npm Manual](#npm-manual)
  - [nvm install](#nvm-install)
  - [doctoc install](#doctoc-install)
- [Time Tracking Tool Manual](#time-tracking-tool-manual)
  - [ActivityWatch](#activitywatch)
    - [Install Page](#install-page)
      - [Zip](#zip)
      - [Installer setup .exe](#installer-setup-exe)
      - [Launch App](#launch-app)
  - [ManicTime](#manictime)
    - [Install Page](#install-page-1)
      - [Zip](#zip-1)
      - [Installer setup .exe](#installer-setup-exe-1)
      - [Launch App](#launch-app-1)
  - [Toggle Track (SaaS:Must Google Acount)](#toggle-track-saasmust-google-acount)
    - [Install Page](#install-page-2)
      - [Installer setup .exe](#installer-setup-exe-2)
      - [Launch App](#launch-app-2)

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
---

## Windows Terminal Install

> <https://www.microsoft.com/ja-jp/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab>

On Windows Terminal

```bash
# settings default distro
wsl -s Ubuntu-20.04

# settings default distro view
wsl -l

# launch wsl
wsl
```

---

Windows Terminal Settings

```bash
Ctrl + ,
```

```bash
⚙ JSON ファイルを開く
```

Copy And Paste

> <https://github.com/2f0833e717/dotfile/blob/master/WindowsTerminalSettings/settings.json>

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

git config --global rebase.autosquash true
# or
git config --local rebase.autosquash true

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

## github commit rebase/autoSquash

```bash
git commit --fixup {commit-hash/HEAD/branch-name}
git rebase -i --autosquash {commit-hash/HEAD/branch-name}
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

## Python venv

```bash
# install venv
sudo apt-get install python3-venv

# create env
python3 -m venv env

# login env
source env/bin/activate
# or
. env/bin/activate

# exit env
deactivate
# or
source ~/.bashrc
```

## Python virtualenv

```bash
# install virtualenv
sudo pip install virtualenv

# virsion
virtualenv --version

# create env
virtualenv env

# login env
source env/bin/activate
# or
. env/bin/activate

# exit env
deactivate
# or
source ~/.bashrc
```

## pip bug update

```bash
# pip bug update
pip install --upgrade pip setuptools
```

## docker-compose install

```bash
# docker-compose install
pip install docker-compose

# view docker-compose version
docker-compose -v
```

## Python fix library version

```bash
sudo -H pip install -I six
sudo pip uninstall docker-compose
sudo pip install -I docker-compose
```

---

# Language setup

```bash
# TBD
```

---

## Golang setup

Golang playground

<https://play.golang.org/>

```bash
# TBD
```

---

## Java setup

Java playground

<https://code.labstack.com/java>

```bash
# TBD
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

---

# Time Tracking Tool Manual

## ActivityWatch

### Install Page
> <https://github.com/ActivityWatch/activitywatch/releases>

---

#### Zip
> <https://github.com/ActivityWatch/activitywatch/releases/download/v0.10.0/activitywatch-v0.10.0-windows-x86_64.zip>

activitywatch-v0.10.0-windows-x86_64.zip

---

#### Installer setup .exe
> <https://github.com/ActivityWatch/activitywatch/releases/download/v0.10.0/activitywatch-v0.10.0-windows-x86_64-setup.exe>

activitywatch-v0.10.0-windows-x86_64-setup.exe

---

#### Launch App

```
aw-qt.exe
```

> <http://localhost:5600/#/>

> <http://localhost:5600/#/timeline>

> <http://localhost:5600/#/settings>

Duration default value => 1h

> <http://localhost:5600/#/activity/{hostname}/view/>

Customize View Area.

---

## ManicTime


### Install Page

> <https://www.manictime.com/download/>

---

#### Zip
> <https://cdn.manictime.com/setup/v4_6_16_0/ManicTimeUsb.zip>

ManicTimeUsb.zip

---

#### Installer setup .exe
> <https://cdn.manictime.com/setup/v4_6_16_0/ManicTime.exe>

ManicTime.exe

---

#### Launch App

```
ManicTime.exe
```

```
(設定)
=> ManicTimeをこのPCでのみ使用(無料オプションを含む)
=> スタンダード(無料)
   無料版。一部の機能はご利用いただけません。
=> 次へ
続けますか
=> はい
ManicTimeの設定が正常に完了しました。
=> OK
```

```
(GUI)
追跡
[▶開始].click

or

(taskbar-menu)
[追跡を開始].click
```

---

## Toggle Track (SaaS:Must Google Acount)

### Install Page

#### Installer setup .exe
> <https://toggl.com/track/toggl-desktop/downloads/TogglTrack-windows64.exe>

TogglTrack-windows64.exe

---

#### Launch App

```
C:\Users\{user}\AppData\Local\TogglDesktop
TogglDesktop.exe
```

```
(設定)
=> Record activitiy (i) => ON(toggle)
```

---

