**Language:** English | [فارسی](../fa/01b-domains.md)

---

<div align="center">

[← Previous: Idea & product](./01-idea-product.md) &nbsp;|&nbsp; [Next: Stack & architecture →](./02-stack-architecture.md)

</div>

# 01b — Buying a domain & domain types

## Goal
Choose and buy a domain, then point it at Cloudflare (or your DNS).

## Common TLDs

| TLD | Notes |
|---|---|
| `.com` | Global default, easy for users |
| `.ir` | Iran registry (NIC.ir), local rules/docs |
| `.dev` / `.app` | HTTPS-minded; often stricter |
| `.net` / `.org` | Fine alternatives if `.com` taken |

## Where to buy
- **NIC.ir** for `.ir`
- International registrars (Namecheap, Cloudflare Registrar, Google Domains successors, etc.)
- Prefer registrars that let you edit **nameservers** freely

## Steps (generic)

1. Search availability
2. Register 1–2 years
3. Enable auto-renew if you can
4. Set nameservers to Cloudflare (or keep registrar DNS)
5. Create DNS records later (chapter 07)

## Useful DNS record types (preview)

| Type | Use |
|---|---|
| `A` | Domain → IPv4 |
| `AAAA` | Domain → IPv6 |
| `CNAME` | Alias (`www` → apex) |
| `TXT` | Verification / SPF |
| `MX` | Email |

## Mistakes
- Pointing `A` to a **private** LAN IP (`192.168.x.x`) on public DNS
- Forgetting `www`
- Changing NS then testing before propagation finishes

---

<div align="center">

[← Previous: Idea & product](./01-idea-product.md) &nbsp;|&nbsp; [Home](../README.md) &nbsp;|&nbsp; [Next: Stack & architecture →](./02-stack-architecture.md)

</div>
