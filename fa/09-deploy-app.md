**زبان:** [English](../en/09-deploy-app.md) | فارسی

---

<div align="center">

[← قبلی: ریورس‌پراکسی](./08-reverse-proxy.md) &nbsp;|&nbsp; [بعدی: امنیت و بکاپ →](./10-security-backup.md)

</div>

# 09 — دیپلوی اپ روی سرور

## هدف
پروسه پروداکشن دائمی پشت nginx.

## ۱) Env

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

## ۲) نصب و migrate و build

```bash
npm ci
npx prisma migrate deploy
npm run build
```

## ۳) واحد systemd

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

## ۴) آپدیت بعدی

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

[← قبلی: ریورس‌پراکسی](./08-reverse-proxy.md) &nbsp;|&nbsp; [خانه](../README.FA.md) &nbsp;|&nbsp; [بعدی: امنیت و بکاپ →](./10-security-backup.md)

</div>
