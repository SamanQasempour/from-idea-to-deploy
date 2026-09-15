**Language:** English | [فارسی](../fa/09-deploy-app.md)

---

<div align="center">

[← Previous: Reverse proxy](./08-reverse-proxy.md) &nbsp;|&nbsp; [Next: Security & backup →](./10-security-backup.md)

</div>

# 09 — Deploy the app on the server

## Goal
Production process running forever behind nginx.

## 1) Env

```bash
cd /var/www/app
cp .env.example .env
nano .env
```

```env
DATABASE_URL="postgresql://app:STRONG@127.0.0.1:5432/app?schema=public"
NEXTAUTH_URL="https://example.com"
NEXTAUTH_SECRET="long-random"
CRON_SECRET="long-random"
TRUST_PROXY=1
```

## 2) Install & migrate & build

```bash
npm ci
npx prisma migrate deploy
# seed only if intentional
npm run build
```

## 3) systemd unit

`/etc/systemd/system/app.service`:

```ini
[Unit]
Description=Web App
After=network.target docker.service

[Service]
Type=simple
WorkingDirectory=/var/www/app
EnvironmentFile=/var/www/app/.env
ExecStart=/usr/bin/npm run start
Restart=always
User=USER
Group=USER

[Install]
WantedBy=multi-user.target
```

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now app
sudo systemctl status app --no-pager
curl -I http://127.0.0.1:43123
```

## 4) Update later

```bash
cd /var/www/app
git pull
npm ci
npx prisma migrate deploy
npm run build
sudo systemctl restart app
```

---

<div align="center">

[← Previous: Reverse proxy](./08-reverse-proxy.md) &nbsp;|&nbsp; [Home](../README.md) &nbsp;|&nbsp; [Next: Security & backup →](./10-security-backup.md)

</div>
