**Language:** English | [فارسی](../fa/03b-github-auth.md)

---

<div align="center">

[← Previous: Git & GitHub](./03-git-github.md) &nbsp;|&nbsp; [Next: Local environment →](./04-local-environment.md)

</div>

# 03b — GitHub auth: token & SSH

## Goal
Stop typing username/password on every `git pull`.

## Option A — Personal Access Token + store (quick)

1. GitHub → Settings → Developer settings → Personal access tokens (classic)
2. Generate token with `repo` scope
3. On the machine:

```bash
git config --global credential.helper store
git pull https://github.com/YOU/YOUR-REPO.git main
# Username: YOU
# Password: paste TOKEN (not account password)
```

Credentials save to `~/.git-credentials`.

> If a token was ever pasted in chat, **revoke it** and create a new one.

## Option B — SSH key (recommended on servers)

```bash
ssh-keygen -t ed25519 -C "server-deploy" -f ~/.ssh/id_ed25519 -N ""
cat ~/.ssh/id_ed25519.pub
```

Add the public key in GitHub → **SSH and GPG keys**.

```bash
cd /var/www/app
git remote set-url origin git@github.com:YOU/YOUR-REPO.git
ssh -T git@github.com
git pull
```

## Compare

| Method | Pros | Cons |
|---|---|---|
| Token + store | Fast | Token file on disk |
| SSH key | Best for servers | One-time key setup |

---

<div align="center">

[← Previous: Git & GitHub](./03-git-github.md) &nbsp;|&nbsp; [Home](../README.md) &nbsp;|&nbsp; [Next: Local environment →](./04-local-environment.md)

</div>
