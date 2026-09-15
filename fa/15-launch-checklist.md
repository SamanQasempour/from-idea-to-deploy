**زبان:** [English](../en/15-launch-checklist.md) | فارسی

---

<div align="center">

[← قبلی: عیب‌یابی](./11-troubleshooting.md) &nbsp;|&nbsp; [خانه راهنما →](../README.FA.md)

</div>

# 15 — چک‌لیست لانچ

## قبل از دادن لینک به دیگران

### محصول
- [ ] جریان اصلی روی موبایل و دسکتاپ کار می‌کند
- [ ] حالت خالی/خطا قابل فهم است
- [ ] رمزهای seed روی پرود نمانده

### دامنه و CDN
- [ ] `https://example.com` باز می‌شود
- [ ] `www` کار می‌کند یا ریدایرکت دارد
- [ ] حالت SSL کلودفلر با Origin جور است
- [ ] Always HTTPS روشن است

### سرور
- [ ] `systemctl is-active app` → active
- [ ] migrate تمیز است
- [ ] دیسک برای آپلود و build جا دارد
- [ ] Postgres عمومی نیست

### عملیات
- [ ] بکاپ یک‌بار موفق بوده
- [ ] cron نصب شده (در صورت نیاز)
- [ ] می‌توانید SSH بزنید و لاگ بخوانید

### بهداشت امنیت
- [ ] secretهای قوی در `.env`
- [ ] احراز گیت‌هاب با SSH یا توکن ذخیره‌شده

## دستور آخر

```bash
cd /var/www/app
git pull
npm ci
npx prisma migrate deploy
npm run build
sudo systemctl restart app
curl -I https://example.com
```

موفق باشید — ۲۴ ساعت اول را مانیتور کنید و یک کامیت rollback دم دست داشته باشید.

---

<div align="center">

[← قبلی: عیب‌یابی](./11-troubleshooting.md) &nbsp;|&nbsp; [خانه](../README.FA.md)

</div>
