# github cli install
install manual
> https://github.com/cli/cli/blob/trunk/docs/install_linux.md

```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key C99B11DEB97541F0
sudo apt-add-repository https://cli.github.com/packages
sudo apt update
sudo apt install gh

gh auth login
```

> https://docs.github.com/ja/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token

```bash
cd {project-root-directory}
gh repo create {repo-name}
```


# github ssh connnection
> https://qiita.com/shizuma/items/2b2f873a0034839e47ce

# github get repositorys
```bash
curl -f -I -L https://api.github.com/users/2f0833e717/repos
curl -f -s -L https://api.github.com/users/2f0833e717/repos | grep "clone_url"
```

