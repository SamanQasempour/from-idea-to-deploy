**زبان:** [English](../en/03-git-github.md) | فارسی

---

<div align="center">

[← قبلی: استک و معماری](./02-stack-architecture.md) &nbsp;|&nbsp; [بعدی: احراز هویت گیت‌هاب →](./03b-github-auth.md)

</div>

# 03 — گیت و ریپوی گیت‌هاب

## هدف
پروژه را روی گیت‌هاب بگذارید و امن push/pull کنید.

## اولین‌بار روی لپ‌تاپ

```bash
cd /path/to/project
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOU/YOUR-REPO.git
git push -u origin main
```

## ضروریات `.gitignore`

```gitignore
node_modules/
.next/
.env
.env.local
backups/
storage/private/**
```

## کار روزمره

```bash
git status
git add -A
git commit -m "توضیح تغییر"
git push
```

## بعداً روی سرور

```bash
cd /var/www/app
git pull origin main
```

بعد از فصل 03b، remote از نوع SSH بهتر است.

---

<div align="center">

[← قبلی: استک و معماری](./02-stack-architecture.md) &nbsp;|&nbsp; [خانه](../README.FA.md) &nbsp;|&nbsp; [بعدی: احراز هویت گیت‌هاب →](./03b-github-auth.md)

</div>
