**Language:** English | [فارسی](../fa/07-cloudflare-dns-ssl.md)

---

<div align="center">

[← Previous: Modem & ports](./06-modem-port-forward.md) &nbsp;|&nbsp; [Next: Reverse proxy →](./08-reverse-proxy.md)

</div>

# 07 — Cloudflare DNS & SSL

## Goal
`https://example.com` reaches your origin through Cloudflare.

## Add the site
1. [dash.cloudflare.com](https://dash.cloudflare.com) → **Add a domain**
2. Free plan
3. Replace registrar nameservers with Cloudflare NS (e.g. NIC.ir DNS settings)
4. Wait until status is **Active**

## DNS records

| Type | Name | Content | Proxy |
|---|---|---|---|
| A | `@` | `PUBLIC_IP` | Proxied (orange) |
| CNAME | `www` | `example.com` | Proxied |

## SSL mode

| Mode | When |
|---|---|
| **Flexible** | Origin only speaks HTTP:80 (quick start) |
| **Full** | Origin has any cert on 443 |
| **Full (strict)** | Origin has valid/public or Cloudflare Origin CA cert |

Also enable **Always Use HTTPS**.

## App env

```env
NEXTAUTH_URL="https://example.com"
TRUST_PROXY=1
```

## Mistakes
- A record to LAN IP
- SSL Full while origin has nothing on 443 → errors
- Testing before NS is Active

---

<div align="center">

[← Previous: Modem & ports](./06-modem-port-forward.md) &nbsp;|&nbsp; [Home](../README.md) &nbsp;|&nbsp; [Next: Reverse proxy →](./08-reverse-proxy.md)

</div>
