**زبان:** [English](../en/04-local-environment.md) | فارسی

---

<div align="center">

[← قبلی: احراز هویت گیت‌هاب](./03b-github-auth.md) &nbsp;|&nbsp; [بعدی: آماده‌سازی VM →](./05-prepare-vm.md)

</div>

# 04 — محیط توسعه لوکال

## هدف
قبل از سرور، اپ را روی لپ‌تاپ اجرا کنید.

## پیش‌نیاز
- Node.js 20+
- Docker (اختیاری برای Postgres) یا Postgres محلی
- Git

## جریان معمول

```bash
cp .env.example .env
# DATABASE_URL و NEXTAUTH_URL=http://127.0.0.1:43123 و secretها

docker compose up -d postgres
npm ci
npx prisma migrate deploy
npm run db:seed
npm run dev
```

آدرس: `http://127.0.0.1:43123` (یا پورت اسکریپت پروژه).

## نمونه `.env` لوکال

```env
DATABASE_URL="postgresql://app:app@127.0.0.1:5432/app?schema=public"
NEXTAUTH_URL="http://127.0.0.1:43123"
NEXTAUTH_SECRET="dev-only-change-me"
```

## تمام وقتی
- صفحه اصلی باز می‌شود
- ورود با کاربر seed کار می‌کند
- خطای اتصال DB ندارید

---

<div align="center">

[← قبلی: احراز هویت گیت‌هاب](./03b-github-auth.md) &nbsp;|&nbsp; [خانه](../README.FA.md) &nbsp;|&nbsp; [بعدی: آماده‌سازی VM →](./05-prepare-vm.md)

</div>
