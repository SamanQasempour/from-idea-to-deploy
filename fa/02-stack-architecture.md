**زبان:** [English](../en/02-stack-architecture.md) | فارسی

---

<div align="center">

[← قبلی: دامنه](./01b-domains.md) &nbsp;|&nbsp; [بعدی: گیت و گیت‌هاب →](./03-git-github.md)

</div>

# 02 — استک و معماری ساده

## هدف
استک ساده‌ای انتخاب کنید که روی یک VM جا شود.

## پیش‌فرض پیشنهادی

```text
مرورگر → Cloudflare → nginx (یا Caddy) → اپ Node (127.0.0.1:PORT)
                                         ↘ PostgreSQL (فقط localhost)
```

## چرا این شکل
- HTTPS لبه با Cloudflare
- اپ فقط روی localhost گوش می‌دهد
- دیتابیس به اینترنت باز نیست

## کی Vercel alone سخت می‌شود
آپلود فایل روی دیسک محلی به **دیسک پایدار** نیاز دارد؛ برای MVP یک VPS ساده‌تر است.

## سرویس‌های حداقلی

| سرویس | نقش |
|---|---|
| پروسه اپ | Next.js / Node API |
| Postgres | داده |
| ریورس‌پراکسی | دامنه + TLS |
| Cron | جاب شبانه / بکاپ |

## پورت‌های نمونه

```text
App:      127.0.0.1:43123
Postgres: 127.0.0.1:5432
HTTP:     0.0.0.0:80
HTTPS:    0.0.0.0:443
SSH:      public:2202 → VM:22
```

---

<div align="center">

[← قبلی: دامنه](./01b-domains.md) &nbsp;|&nbsp; [خانه](../README.FA.md) &nbsp;|&nbsp; [بعدی: گیت و گیت‌هاب →](./03-git-github.md)

</div>
