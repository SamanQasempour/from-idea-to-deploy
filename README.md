# From Idea to Deploy

![From Idea to Deploy](./assets/banner-from-idea-to-deploy-en.png)

> A practical, general guide to take a web app from idea → GitHub → server → domain → Cloudflare → production.
> Not tied to one product brand — use these steps for any Node/Next-style app on a VPS.

**Language:** English | [فارسی](./README.FA.md)

---



## What you will learn

| Stage | What you get |
|---|---|
| Idea & domain | Clear MVP + how to buy/configure a domain |
| Hosting choices | Shared vs VPS vs home modem setups |
| GitHub | Repo, token, SSH so `git pull` never asks again |
| Local & VM | Run the app locally, then on a Linux VM |
| Network | Modem port forward + Cloudflare DNS/SSL |
| Multi-site | Reverse proxy when several sites share one public IP |
| Ship | systemd deploy, security, backups, troubleshooting |

---

## Chapters

| # | Chapter |
|---|---|
| 00 | [Roadmap & checklist overview](./en/00-roadmap.md) |
| 01 | [Idea & product definition](./en/01-idea-product.md) |
| 01b | [Buying a domain & domain types](./en/01b-domains.md) |
| 02 | [Stack & simple architecture](./en/02-stack-architecture.md) |
| 03 | [Git & GitHub repository](./en/03-git-github.md) |
| 03b | [GitHub auth: token & SSH](./en/03b-github-auth.md) |
| 04 | [Local development environment](./en/04-local-environment.md) |
| 05 | [Prepare the VM](./en/05-prepare-vm.md) |
| 05b | [Hosting & server types](./en/05b-hosting-types.md) |
| 06 | [Modem & port forwarding](./en/06-modem-port-forward.md) |
| 07 | [Cloudflare DNS & SSL](./en/07-cloudflare-dns-ssl.md) |
| 08 | [Reverse proxy for multiple sites](./en/08-reverse-proxy.md) |
| 09 | [Deploy the app on the server](./en/09-deploy-app.md) |
| 10 | [Security, backup & cron](./en/10-security-backup.md) |
| 11 | [Common troubleshooting](./en/11-troubleshooting.md) |
| 15 | [Launch checklist](./en/15-launch-checklist.md) |

---

## How to use this guide

1. Open chapters in order (each page has **Previous / Next** at the top and bottom).
2. Copy commands into your terminal — replace placeholders like `example.com` and `YOUR_IP`.
3. Prefer **SSH keys** for GitHub on the server (see chapter 03b).
4. Never commit real passwords or tokens.

---

## Placeholders used in examples

| Placeholder | Meaning |
|---|---|
| `example.com` | Your domain |
| `USER` | Linux username on the VM |
| `PUBLIC_IP` | Public IPv4 of your network/datacenter |
| `192.168.100.10` | Private LAN IP of your VM |
| `/var/www/app` | App directory on the server |

---

## Start here

→ **[00 — Roadmap](./en/00-roadmap.md)**
# from-idea-to-deploy
