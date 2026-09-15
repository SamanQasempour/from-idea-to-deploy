**Language:** English | [فارسی](../fa/08-reverse-proxy.md)

---

<div align="center">

[← Previous: Cloudflare DNS & SSL](./07-cloudflare-dns-ssl.md) &nbsp;|&nbsp; [Next: Deploy the app →](./09-deploy-app.md)

</div>

# 08 — Reverse proxy for multiple sites

## Goal
Share one public IP / one nginx that already owns ports 80/443, and route by hostname.

## Pattern

```text
Internet → Modem 80/443 → Host A (nginx)
                           ├─ example-a.com → local app A
                           └─ example-b.com → http://192.168.100.20:80  (Host B)
```

## nginx server block on Host A

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

## Docker nginx note
If Host A uses `nginx:alpine` with a bind-mounted `conf.d/`, add a new file there and reload:

```bash
docker exec NAME nginx -t
docker exec NAME nginx -s reload
```

## Test on Host A

```bash
curl -I -H "Host: example-b.com" http://127.0.0.1
curl -I -H "Host: example-a.com" http://127.0.0.1
```

---

<div align="center">

[← Previous: Cloudflare DNS & SSL](./07-cloudflare-dns-ssl.md) &nbsp;|&nbsp; [Home](../README.md) &nbsp;|&nbsp; [Next: Deploy the app →](./09-deploy-app.md)

</div>
