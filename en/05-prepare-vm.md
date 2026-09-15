**Language:** English | [فارسی](../fa/05-prepare-vm.md)

---

<div align="center">

[← Previous: Local environment](./04-local-environment.md) &nbsp;|&nbsp; [Next: Hosting types →](./05b-hosting-types.md)

</div>

# 05 — Prepare the VM

## Goal
A clean Ubuntu (or similar) VM ready for Node + Docker + nginx.

## SSH in

```bash
ssh -p 2202 USER@PUBLIC_IP
```

## Baseline packages

```bash
sudo apt update
sudo apt install -y git curl ca-certificates nginx
# Node 20 via NodeSource or nvm — follow current docs for your distro
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs
# Docker (optional)
curl -fsSL https://get.docker.com | sudo sh
sudo usermod -aG docker $USER
```

## App directory

```bash
sudo mkdir -p /var/www
sudo chown "$USER":"$USER" /var/www
cd /var/www
git clone git@github.com:YOU/YOUR-REPO.git app
cd app
```

## Disk sanity

```bash
df -h /
free -h
nproc
```

If root is tiny, extend LVM **before** `npm ci` / `npm run build`.

## Firewall idea

```bash
sudo ufw allow OpenSSH
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
```

Do **not** expose Postgres `5432` to the world.

---

<div align="center">

[← Previous: Local environment](./04-local-environment.md) &nbsp;|&nbsp; [Home](../README.md) &nbsp;|&nbsp; [Next: Hosting types →](./05b-hosting-types.md)

</div>
