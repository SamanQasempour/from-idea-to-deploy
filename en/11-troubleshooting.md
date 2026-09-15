**Language:** English | [فارسی](../fa/11-troubleshooting.md)

---

<div align="center">

[← Previous: Security & backup](./10-security-backup.md) &nbsp;|&nbsp; [Next: Launch checklist →](./15-launch-checklist.md)

</div>

# 11 — Common troubleshooting

## Matrix

| Symptom | Likely cause | Check |
|---|---|---|
| Domain shows another site | Host header / wrong nginx `server_name` | `curl -I -H "Host: example.com" http://127.0.0.1` |
| Cloudflare 521/522 | Origin down or port closed | `systemctl status app nginx`; modem forwards |
| Login broken after domain | Wrong `NEXTAUTH_URL` | Must be exact `https://example.com` |
| Page crashes after migrate | Schema drift / missing column | App logs: `journalctl -u app -n 100` |
| `git pull` asks password | No token/SSH | Chapter 03b |
| Disk full mid-build | Tiny root FS | `df -h`; extend LVM |
| Wrong site on same IP | Missing/priority `server_name` | List sites: `nginx -T \| grep server_name` |
| HTTPS redirect loop | SSL mode vs origin mismatch | Flexible↔HTTP:80 or Full↔443 |
| 502 Bad Gateway | App not listening / wrong `proxy_pass` | `ss -lntp \| grep PORT`; curl localhost |

## Useful commands

```bash
sudo systemctl status app nginx --no-pager
sudo journalctl -u app -n 80 --no-pager
curl -I http://127.0.0.1:43123
curl -I -H "Host: example.com" http://127.0.0.1
curl -I https://example.com
npx prisma migrate status
dig +short example.com
```

## Rule
Fix **one layer** at a time: DNS → modem → nginx → app → DB.

---

<div align="center">

[← Previous: Security & backup](./10-security-backup.md) &nbsp;|&nbsp; [Home](../README.md) &nbsp;|&nbsp; [Next: Launch checklist →](./15-launch-checklist.md)

</div>
