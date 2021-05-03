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
    - [apt update](#apt-update)
    - [homebrew install](#homebrew-install)
    - [brew update](#brew-update)
  - [wsl uninstall](#wsl-uninstall)
- [Github Manual](#github-manual)
  - [github ssh connnection](#github-ssh-connnection)
  - [setting .gitconfig](#setting-gitconfig)
  - [github cli install](#github-cli-install)
  - [github get repositorys](#github-get-repositorys)
  - [git commit message sample](#git-commit-message-sample)
- [npm Manual](#npm-manual)
  - [nvm install](#nvm-install)
  - [doctoc install](#doctoc-install)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# WSL Manual

## wsl install

> <https://docs.microsoft.com/ja-jp/windows/wsl/install-win10>

* Download on Microsoft Store
* Launch on Microsoft Store

```bash
# Launch Ubuntu-20.04 Terminal

# UserName
ubuntu

# Password
ubuntu

exit
```

```bash
# Windows Terminal

wsl -l
wsl -s Ubuntu-20.04
wsl
```

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
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/ubuntu/.profile
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"

# reload wsl
exit
wsl
```

### brew update
```bash
brew update ; \
brew upgrade ; \
brew doctor ; \
# brew prune  # old command @ Homebrew 1.9.0
brew cleanup ;
```

---

## wsl uninstall
* {Win-key} + i
* application
* serch `Ubuntu-20.04`
* uninstall

---

# Github Manual

## github ssh connnection

> <https://qiita.com/shizuma/items/2b2f873a0034839e47ce>

```bash
ssh-keygen -t rsa

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
{Enter x 3}

# Windows(wsl)
clip.exe < ~/.ssh/id_rsa.pub
```

Move to
> <https://github.com/settings/keys>

* [New SSH Key]
* id_rsa
* Ctrl + V
* [Add SSH Key]

```bash
# vi ~/.ssh/config
Host github github.com
  HostName github.com
  IdentityFile ~/.ssh/id_rsa
  User git
```

```bash
ssh -T github

# Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
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

## github get repositorys

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

# npm Manual

## nvm install

```bash
git clone https://github.com/creationix/nvm.git ~/.nvm
source ~/.nvm/nvm.sh
nvm install --lts
nvm -v
```

```bash
# ~/.bash_profile
if [ -s ~/.nvm/nvm.sh ]; then
  source ~/.nvm/nvm.sh
fi
```

---

## doctoc install
> <https://github.com/thlorenz/doctoc>

```bash
npm install -g doctoc
mkdir -p .github/workflows
touch .github/workflows/toc.yml
```

doctoc ettings
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
