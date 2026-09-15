**زبان:** [English](../en/08-reverse-proxy.md) | فارسی

---

<div align="center">

[← قبلی: کلودفلر DNS و SSL](./07-cloudflare-dns-ssl.md) &nbsp;|&nbsp; [بعدی: دیپلوی اپ →](./09-deploy-app.md)

</div>

# 08 — ریورس‌پراکسی چندسایت

## هدف
یک IP عمومی / یک nginx که 80/443 دارد، ترافیک را با hostname جدا کند.

## الگو

```text
اینترنت → مودم 80/443 → میزبان A (nginx)
                         ├─ example-a.com → اپ محلی A
                         └─ example-b.com → http://192.168.100.20:80  (میزبان B)
```

## بلاک nginx روی میزبان A

```nginx
server {
  listen 80;
  server_name example-b.com www.example-b.com;
  client_max_body_size 20M;

  location / {
    proxy_pass http://192.168.100.20:80;
    proxy_http_version 1.1;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
  }
}
```

```bash
sudo nginx -t && sudo systemctl reload nginx
```

## نکته nginx داکری
اگر `conf.d` بایند شده، فایل جدید بسازید و reload کنید:

```bash
docker exec NAME nginx -t
docker exec NAME nginx -s reload
```

## تست

```bash
curl -I -H "Host: example-b.com" http://127.0.0.1
curl -I -H "Host: example-a.com" http://127.0.0.1
```

---

<div align="center">

[← قبلی: کلودفلر DNS و SSL](./07-cloudflare-dns-ssl.md) &nbsp;|&nbsp; [خانه](../README.FA.md) &nbsp;|&nbsp; [بعدی: دیپلوی اپ →](./09-deploy-app.md)

</div>
