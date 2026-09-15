**زبان:** [English](../en/05-prepare-vm.md) | فارسی

---

<div align="center">

[← قبلی: محیط لوکال](./04-local-environment.md) &nbsp;|&nbsp; [بعدی: انواع هاست →](./05b-hosting-types.md)

</div>

# 05 — آماده‌سازی VM

## هدف
یک VM تمیز برای Node + Docker + nginx.

## ورود SSH

```bash
ssh -p 2202 USER@PUBLIC_IP
```

## بسته‌های پایه

```bash
sudo apt update
sudo apt install -y git curl ca-certificates nginx
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs
curl -fsSL https://get.docker.com | sudo sh
sudo usermod -aG docker $USER
```

## پوشه اپ

```bash
sudo mkdir -p /var/www
sudo chown "$USER":"$USER" /var/www
cd /var/www
git clone git@github.com:YOU/YOUR-REPO.git app
cd app
```

## سلامت دیسک

```bash
df -h /
free -h
nproc
```

اگر ریشه کوچک است، قبل از `npm ci` / build فضای LVM را زیاد کنید.

## فایروال

```bash
sudo ufw allow OpenSSH
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
```

پورت `5432` را به اینترنت باز نکنید.

---

<div align="center">

[← قبلی: محیط لوکال](./04-local-environment.md) &nbsp;|&nbsp; [خانه](../README.FA.md) &nbsp;|&nbsp; [بعدی: انواع هاست →](./05b-hosting-types.md)

</div>
