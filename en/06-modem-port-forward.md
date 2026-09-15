**Language:** English | [فارسی](../fa/06-modem-port-forward.md)

---

<div align="center">

[← Previous: Hosting types](./05b-hosting-types.md) &nbsp;|&nbsp; [Next: Cloudflare DNS & SSL →](./07-cloudflare-dns-ssl.md)

</div>

# 06 — Modem & port forwarding

## Goal
Reach an internal VM from the public internet through a router/modem.

## Terms

| Term | Example |
|---|---|
| Public IP | `PUBLIC_IP` on the WAN |
| Private IP | `192.168.100.10` on the VM |
| Port forward | WAN `:80` → LAN `192.168.100.10:80` |

## Huawei-style menus (names vary)
**Forward Rules → Port Mapping Configuration**

## Recommended rules

| Name | External | Internal host | Internal port | Proto |
|---|---|---|---|---|
| web-http | 80 | `192.168.100.10` | 80 | TCP |
| web-https | 443 | `192.168.100.10` | 443 | TCP |
| ssh-vm | 2202 | `192.168.100.10` | 22 | TCP |

## Critical conflict rule
**One external port → one internal host.**  
If `web-http` already points to another server, do **not** steal ports 80/443. Use reverse proxy on that server instead (chapter 08).

## DHCP reservation
Pin the VM MAC to a fixed LAN IP so forwards do not break after reboot.

## Test from mobile data (not LAN Wi‑Fi)

```bash
curl -I http://PUBLIC_IP
```

---

<div align="center">

[← Previous: Hosting types](./05b-hosting-types.md) &nbsp;|&nbsp; [Home](../README.md) &nbsp;|&nbsp; [Next: Cloudflare DNS & SSL →](./07-cloudflare-dns-ssl.md)

</div>
