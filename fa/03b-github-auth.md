**زبان:** [English](../en/03b-github-auth.md) | فارسی

---

<div align="center">

[← قبلی: گیت و گیت‌هاب](./03-git-github.md) &nbsp;|&nbsp; [بعدی: محیط لوکال →](./04-local-environment.md)

</div>

# 03b — احراز هویت گیت‌هاب: توکن و SSH

## هدف
دیگر برای هر `git pull` یوزر/پسورد ندهید.

## روش A — توکن + ذخیره (سریع)

1. GitHub → Settings → Developer settings → Personal access tokens (classic)
2. توکن با دسترسی `repo`
3. روی ماشین:

```bash
git config --global credential.helper store
git pull https://github.com/YOU/YOUR-REPO.git main
# Username: YOU
# Password: توکن (نه رمز حساب)
```

در `~/.git-credentials` ذخیره می‌شود.

> اگر توکن جایی لو رفته، **Revoke** کنید و جدید بسازید.

## روش B — کلید SSH (پیشنهادی برای سرور)

```bash
ssh-keygen -t ed25519 -C "server-deploy" -f ~/.ssh/id_ed25519 -N ""
cat ~/.ssh/id_ed25519.pub
```

کلید عمومی را در GitHub → **SSH and GPG keys** بگذارید.

```bash
cd /var/www/app
git remote set-url origin git@github.com:YOU/YOUR-REPO.git
ssh -T git@github.com
git pull
```

## مقایسه

| روش | مزیت | عیب |
|---|---|---|
| توکن + store | سریع | فایل توکن روی دیسک |
| SSH | مناسب سرور | یک‌بار تنظیم کلید |

---

<div align="center">

[← قبلی: گیت و گیت‌هاب](./03-git-github.md) &nbsp;|&nbsp; [خانه](../README.FA.md) &nbsp;|&nbsp; [بعدی: محیط لوکال →](./04-local-environment.md)

</div>
