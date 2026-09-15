**Language:** English | [فارسی](../fa/15-launch-checklist.md)

---

<div align="center">

[← Previous: Troubleshooting](./11-troubleshooting.md) &nbsp;|&nbsp; [Guide home →](../README.md)

</div>

# 15 — Launch checklist

## Before you tell anyone the URL

### Product
- [ ] Core user flow works on mobile and desktop
- [ ] Empty / error states are understandable
- [ ] Seed/demo passwords are not left on production

### Domain & CDN
- [ ] `https://example.com` loads
- [ ] `www` redirects or works
- [ ] Cloudflare SSL mode matches origin
- [ ] Always HTTPS on

### Server
- [ ] `systemctl is-active app` → active
- [ ] `migrate deploy` clean
- [ ] Disk has free space for uploads + builds
- [ ] Postgres not public

### Ops
- [ ] Backup script ran once successfully
- [ ] Cron installed (if needed)
- [ ] You can SSH in and read logs

### Security hygiene
- [ ] Strong secrets in `.env`
- [ ] GitHub auth via SSH or stored token (not chat-pasted secrets)

## Ship command (last mile)

```bash
cd /var/www/app
git pull
npm ci
npx prisma migrate deploy
npm run build
sudo systemctl restart app
curl -I https://example.com
```

Congrats — now monitor for 24h and keep a rollback commit handy.

---

<div align="center">

[← Previous: Troubleshooting](./11-troubleshooting.md) &nbsp;|&nbsp; [Home](../README.md)

</div>
