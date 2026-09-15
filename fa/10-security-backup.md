**زبان:** [English](../en/10-security-backup.md) | فارسی

---

<div align="center">

[← قبلی: دیپلوی اپ](./09-deploy-app.md) &nbsp;|&nbsp; [بعدی: عیب‌یابی →](./11-troubleshooting.md)

</div>

# 10 — امنیت، بکاپ و کرون

## هدف
از حادثه و حمله ساده جان سالم به در ببرید.

## رمزها
- `NEXTAUTH_SECRET` / رمز DB / `CRON_SECRET` قوی
- `.env` را commit نکنید
- توکن لو‌رفته را عوض کنید

## شبکه
- Postgres فقط `127.0.0.1`
- ترجیحاً SSH روی پورت غیرپیش‌فرض
- اپ روی localhost؛ فقط پراکسی عمومی است

## اسکچ بکاپ

```bash
pg_dump "$DATABASE_URL" | gzip > "/var/backups/app-$(date +%F).sql.gz"
# پوشه آپلود خصوصی را هم آرشیو کنید
```

کپی را در صورت امکان **خارج** از همان VM نگه دارید.

## نمونه cron

```cron
15 2 * * * cd /var/www/app && /usr/bin/npm run ops:nightly:http >> /var/log/app-nightly.log 2>&1
30 2 * * * /var/www/app/scripts/backup.sh >> /var/log/app-backup.log 2>&1
```

## هدرها
هدرهای امنیتی روی پراکسی + اپ (HSTS، frame deny، nosniff).

---

<div align="center">

[← قبلی: دیپلوی اپ](./09-deploy-app.md) &nbsp;|&nbsp; [خانه](../README.FA.md) &nbsp;|&nbsp; [بعدی: عیب‌یابی →](./11-troubleshooting.md)

</div>
