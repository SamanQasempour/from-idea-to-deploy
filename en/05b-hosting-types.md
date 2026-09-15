**Language:** English | [فارسی](../fa/05b-hosting-types.md)

---

<div align="center">

[← Previous: Prepare the VM](./05-prepare-vm.md) &nbsp;|&nbsp; [Next: Modem & ports →](./06-modem-port-forward.md)

</div>

# 05b — Hosting & server types

## Goal
Pick the right home for the app.

## Comparison

| Type | Control | Good for | Pain |
|---|---|---|---|
| Shared hosting | Low | Static PHP sites | Bad for custom Node + private uploads |
| VPS / Cloud VM | High | Most SaaS MVPs | You manage OS updates |
| Dedicated | Highest | Heavy load | Cost |
| Serverless (Vercel…) | Easy deploys | Stateless apps | Persistent local files / long jobs |
| Home PC behind modem | Free-ish | Learning / staging | Dynamic IP, power, NAT complexity |

## Minimum for Node + Postgres MVP (rule of thumb)

| Resource | Minimum | Comfortable |
|---|---|---|
| vCPU | 2 | 4 |
| RAM | 4 GB | 8 GB |
| Disk | 40 GB SSD | 80 GB+ |
| OS | Ubuntu 22.04+ | same |

## Iran / abroad / office VM
- Datacenter VPS: public IP on the machine → simpler DNS
- Office/home VM: public IP on modem → port forward (chapter 06)
- Multiple VMs behind one public IP → reverse proxy (chapter 08)

---

<div align="center">

[← Previous: Prepare the VM](./05-prepare-vm.md) &nbsp;|&nbsp; [Home](../README.md) &nbsp;|&nbsp; [Next: Modem & ports →](./06-modem-port-forward.md)

</div>
