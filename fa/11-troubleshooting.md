**زبان:** [English](../en/11-troubleshooting.md) | فارسی

---

<div align="center">

[← قبلی: امنیت و بکاپ](./10-security-backup.md) &nbsp;|&nbsp; [بعدی: چک‌لیست لانچ →](./15-launch-checklist.md)

</div>

# 11 — عیب‌یابی رایج

## جدول

| علامت | علت محتمل | چک |
|---|---|---|
| دامنه سایت دیگر را نشان می‌دهد | Host / `server_name` اشتباه | `curl -I -H "Host: example.com" http://127.0.0.1` |
| Cloudflare 521/522 | Origin خاموش / پورت بسته | `systemctl status`؛ فوروارد مودم |
| لاگین بعد دامنه خراب | `NEXTAUTH_URL` غلط | دقیقاً `https://example.com` |
| صفحه بعد migrate می‌ترکد | اختلاف schema | `journalctl -u app -n 100` |
| `git pull` پسورد می‌خواهد | توکن/SSH نیست | فصل 03b |
| دیسک وسط build پر شد | ریشه کوچک | `df -h`؛ LVM |
| سایت اشتباه روی همان IP | `server_name` اشتباه/اولویت | `nginx -T \| grep server_name` |
| حلقه ریدایرکت HTTPS | ناسازگاری SSL mode و origin | Flexible↔HTTP:80 یا Full↔443 |
| 502 Bad Gateway | اپ گوش نمی‌دهد / `proxy_pass` غلط | `ss -lntp \| grep PORT`؛ curl لوکال |

## دستورهای مفید

```bash
sudo systemctl status app nginx --no-pager
sudo journalctl -u app -n 80 --no-pager
curl -I http://127.0.0.1:43123
curl -I -H "Host: example.com" http://127.0.0.1
curl -I https://example.com
npx prisma migrate status
dig +short example.com
```

## قانون
هر بار **یک لایه**: DNS → مودم → nginx → اپ → DB.

---

<div align="center">

[← قبلی: امنیت و بکاپ](./10-security-backup.md) &nbsp;|&nbsp; [خانه](../README.FA.md) &nbsp;|&nbsp; [بعدی: چک‌لیست لانچ →](./15-launch-checklist.md)

</div>
