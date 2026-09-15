**Language:** English | [فارسی](../fa/04-local-environment.md)

---

<div align="center">

[← Previous: GitHub auth](./03b-github-auth.md) &nbsp;|&nbsp; [Next: Prepare the VM →](./05-prepare-vm.md)

</div>

# 04 — Local development environment

## Goal
Run the app on your laptop before any server work.

## Prerequisites
- Node.js 20+
- Docker (optional, for Postgres) or local Postgres
- Git

## Typical flow

```bash
cp .env.example .env
# edit DATABASE_URL, NEXTAUTH_URL=http://127.0.0.1:43123, secrets

docker compose up -d postgres   # if you use compose
npm ci
npx prisma migrate deploy
npm run db:seed                 # if the project has seed
npm run dev
```

Open `http://127.0.0.1:43123` (or the port in package scripts).

## Sample `.env` (local)

```env
DATABASE_URL="postgresql://app:app@127.0.0.1:5432/app?schema=public"
NEXTAUTH_URL="http://127.0.0.1:43123"
NEXTAUTH_SECRET="dev-only-change-me"
```

## Done when
- Home page loads
- Login works with seed users
- No DB connection errors in the terminal

---

<div align="center">

[← Previous: GitHub auth](./03b-github-auth.md) &nbsp;|&nbsp; [Home](../README.md) &nbsp;|&nbsp; [Next: Prepare the VM →](./05-prepare-vm.md)

</div>
