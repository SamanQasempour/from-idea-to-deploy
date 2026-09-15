**Language:** English | [فارسی](../fa/02-stack-architecture.md)

---

<div align="center">

[← Previous: Domains](./01b-domains.md) &nbsp;|&nbsp; [Next: Git & GitHub →](./03-git-github.md)

</div>

# 02 — Stack & simple architecture

## Goal
Pick a boring stack that you can host on one VM.

## Recommended default (web app)

```text
Browser → Cloudflare → nginx (or Caddy) → Node app (127.0.0.1:PORT)
                                      ↘ PostgreSQL (localhost only)
```

## Why this shape
- Cloudflare terminates user HTTPS at the edge
- App binds to localhost (not the public internet)
- Database never exposed publicly

## When Vercel-only is awkward
Local disk uploads (`storage/`, receipts, private files) need **persistent disk**. A single VPS is simpler for that MVP.

## Minimal services

| Service | Role |
|---|---|
| App process | Next.js / Node API |
| Postgres | Data |
| Reverse proxy | Host routing + TLS |
| Cron | Nightly jobs / backups |

## Sample ports

```text
App:      127.0.0.1:43123
Postgres: 127.0.0.1:5432
HTTP:     0.0.0.0:80
HTTPS:    0.0.0.0:443
SSH:      public:2202 → VM:22
```

---

<div align="center">

[← Previous: Domains](./01b-domains.md) &nbsp;|&nbsp; [Home](../README.md) &nbsp;|&nbsp; [Next: Git & GitHub →](./03-git-github.md)

</div>
