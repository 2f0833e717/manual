# GitHub manual
 
<!-- # Badges -->

[![Github issues](https://img.shields.io/github/issues/2f0833e717/manual)](https://github.com/2f0833e717/manual/issues)
[![Github forks](https://img.shields.io/github/forks/2f0833e717/manual)](https://github.com/2f0833e717/manual/network/members)
[![Github stars](https://img.shields.io/github/stars/2f0833e717/manual)](https://github.com/2f0833e717/manual/stargazers)
[![Github top language](https://img.shields.io/github/languages/top/2f0833e717/manual)](https://github.com/2f0833e717/manual/)
[![Github license](https://img.shields.io/github/license/2f0833e717/manual)](https://github.com/2f0833e717/manual/)

## github cli install

install manual
> <https://github.com/cli/cli/blob/trunk/docs/install_linux.md>

```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key C99B11DEB97541F0
sudo apt-add-repository https://cli.github.com/packages
sudo apt update
sudo apt install gh

gh auth login
```

as browser, ssh

get access-token
> <https://docs.github.com/ja/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token>

```bash
cd {project-root-directory}
gh repo create {repo-name}
```

---

## github ssh connnection

> <https://qiita.com/shizuma/items/2b2f873a0034839e47ce>

---

## github get repositorys

```bash
curl -f -I -L https://api.github.com/users/2f0833e717/repos
```

```bash
curl -f -s -L https://api.github.com/users/2f0833e717/repos | \
grep "clone_url" | \
sed -e "s/\"clone_url\"\:\s\"//" | \
sed -e "s/\"\,$//"
```

---

## github ssh connnection
> <https://qiita.com/shizuma/items/2b2f873a0034839e47ce>
> <https://mseeeen.msen.jp/github-api-get-all-repos-info/>

---

## github cli pullrequest & merge

```bash
gh pr create -f
```

> <https://cli.github.com/manual/gh_pr_create>

```bash
gh pr merge -m
```

> <https://cli.github.com/manual/gh_pr_merge>

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

# Bash manual
> <http://www.tohoho-web.com/ex/shell.html>

---
