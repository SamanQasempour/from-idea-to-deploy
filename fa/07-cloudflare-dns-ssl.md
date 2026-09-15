**زبان:** [English](../en/07-cloudflare-dns-ssl.md) | فارسی

---

<div align="center">

[← قبلی: مودم و پورت](./06-modem-port-forward.md) &nbsp;|&nbsp; [بعدی: ریورس‌پراکسی →](./08-reverse-proxy.md)

</div>

# 07 — کلودفلر، DNS و SSL

## هدف
`https://example.com` از طریق Cloudflare به Origin برسد.

## افزودن سایت
1. [dash.cloudflare.com](https://dash.cloudflare.com) → **Add a domain**
2. پلن Free
3. NS ثبت‌کننده را با NS کلودفلر عوض کنید (مثلاً ایرنیک)
4. صبر تا وضعیت **Active**

## رکوردها

| نوع | نام | محتوا | Proxy |
|---|---|---|---|
| A | `@` | `PUBLIC_IP` | Proxied |
| CNAME | `www` | `example.com` | Proxied |

## حالت SSL

| حالت | کی |
|---|---|
| **Flexible** | Origin فقط HTTP:80 |
| **Full** | Origin روی 443 گواهی دارد |
| **Full (strict)** | گواهی معتبر / Origin CA |

**Always Use HTTPS** را روشن کنید.

## env اپ

```env
NEXTAUTH_URL="https://example.com"
TRUST_PROXY=1
```

## اشتباهات
- A به IP داخلی
- Full بدون 443 روی Origin
- تست قبل از Active شدن NS

---

<div align="center">

[← قبلی: مودم و پورت](./06-modem-port-forward.md) &nbsp;|&nbsp; [خانه](../README.FA.md) &nbsp;|&nbsp; [بعدی: ریورس‌پراکسی →](./08-reverse-proxy.md)

</div>
