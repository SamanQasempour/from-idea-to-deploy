**Language:** English | [فارسی](../fa/00-roadmap.md)

---

<div align="center">

[← Guide home](../README.md) &nbsp;|&nbsp; [Next: Idea & product →](./01-idea-product.md)

</div>

# 00 — Roadmap

## Goal
See the full path before you touch a terminal.

## Success looks like
You know which chapter to open next, and what “done” means for each stage.

## The path (high level)

```text
Idea → Domain → Code + GitHub → Local run → VM
    → Modem/ports (if home/office) → Cloudflare DNS/SSL
    → Reverse proxy (if multi-site) → Deploy → Harden → Launch
```

## Stage checklist

- [ ] MVP written in one page
- [ ] Domain purchased / NS ready
- [ ] Repo on GitHub
- [ ] App runs locally
- [ ] VM reachable over SSH
- [ ] HTTP/HTTPS reach the correct machine
- [ ] App runs under systemd (or similar)
- [ ] Backup + secrets policy

## Tip
Do **network** (modem/DNS) and **app deploy** as separate days if you are new — debugging both at once is painful.

---

<div align="center">

[Home](../README.md) &nbsp;|&nbsp; [Next: Idea & product →](./01-idea-product.md)

</div>
