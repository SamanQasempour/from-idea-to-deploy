**Language:** English | [فارسی](../fa/10-security-backup.md)

---

<div align="center">

[← Previous: Deploy the app](./09-deploy-app.md) &nbsp;|&nbsp; [Next: Troubleshooting →](./11-troubleshooting.md)

</div>

# 10 — Security, backup & cron

## Goal
Survive accidents and basic attacks.

## Secrets
- Strong `NEXTAUTH_SECRET` / DB password / `CRON_SECRET`
- Never commit `.env`
- Rotate tokens leaked in chat

## Network
- Postgres on `127.0.0.1` only
- SSH on a non-default port if possible
- App binds to localhost; only proxy is public

## Backup sketch

```bash
# example: dump DB
pg_dump "$DATABASE_URL" | gzip > "/var/backups/app-$(date +%F).sql.gz"
# also archive private upload dirs if you store files on disk
```

Keep copies **off** the same VM when you can.

## Cron examples

```cron
15 2 * * * cd /var/www/app && /usr/bin/npm run ops:nightly:http >> /var/log/app-nightly.log 2>&1
30 2 * * * /var/www/app/scripts/backup.sh >> /var/log/app-backup.log 2>&1
```

## Headers
Prefer proxy + app security headers (HSTS, frame deny, nosniff).

---

<div align="center">

[← Previous: Deploy the app](./09-deploy-app.md) &nbsp;|&nbsp; [Home](../README.md) &nbsp;|&nbsp; [Next: Troubleshooting →](./11-troubleshooting.md)

</div>
