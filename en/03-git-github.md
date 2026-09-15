**Language:** English | [فارسی](../fa/03-git-github.md)

---

<div align="center">

[← Previous: Stack & architecture](./02-stack-architecture.md) &nbsp;|&nbsp; [Next: GitHub auth →](./03b-github-auth.md)

</div>

# 03 — Git & GitHub repository

## Goal
Put the project on GitHub and push/pull safely.

## First time on laptop

```bash
cd /path/to/project
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOU/YOUR-REPO.git
git push -u origin main
```

## `.gitignore` essentials

```gitignore
node_modules/
.next/
.env
.env.local
backups/
storage/private/**
```

## Daily workflow

```bash
git status
git add -A
git commit -m "Describe the change"
git push
```

## On the server later

```bash
cd /var/www/app
git pull origin main
```

Prefer SSH remotes after chapter 03b.

---

<div align="center">

[← Previous: Stack & architecture](./02-stack-architecture.md) &nbsp;|&nbsp; [Home](../README.md) &nbsp;|&nbsp; [Next: GitHub auth →](./03b-github-auth.md)

</div>
