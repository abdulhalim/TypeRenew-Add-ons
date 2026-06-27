# TypeRenew Add-ons

<p align="center">
  <img src="https://img.shields.io/badge/TypeRenew-v1.5.1-blue.svg" alt="TypeRenew Version">
  <img src="https://img.shields.io/badge/PHP-%3E%3D%208.0-777bb4.svg" alt="PHP Version">
  <img src="https://img.shields.io/badge/License-GPL%20v2-blue.svg" alt="License">
  <img src="https://img.shields.io/badge/Font-OFL%201.1-green.svg" alt="Font License">
  <img src="https://img.shields.io/badge/Languages-fa__IR%20%7C%20en__US-orange.svg" alt="Languages">
  <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg" alt="PRs Welcome">
</p>

<h1 align="center">🌍 TypeRenew Add-ons</h1>

<p align="center">
  <strong>RTL/LTR Default Theme + Complete Persian & English Language Packs + RTL Styles & Vazirmatn Font for TypeRenew Core</strong>
</p>

<p align="center">
  <a href="#english">English</a> •
  <a href="#persian">فارسی</a>
</p>

---

## English

<h2 id="english">🇬🇧 Complete RTL/LTR Support for TypeRenew</h2>



### 📖 Overview

This repository provides **complete RTL/LTR support** with **Persian (fa_IR)** and **English (en_US)** language packs for [TypeRenew](https://www.typerenew.com/) v1.5.1. A lightweight, plugin-free solution that optimizes all TypeRenew sections for Persian-speaking users.

**Core Philosophy:**
- ✅ Minimal core changes (only 2 small PHP code snippets)
- ✅ No external dependencies (Vazirmatn font embedded as base64 in CSS)
- ✅ Zero impact on other languages (CSS loads only when Persian is active)

### 📁 Repository Structure

```
TypeRenew-Add-ons/
├── README.md                           # This file
├── TypeRenew_admin/                    # Admin Persian package
│   ├── README.md
│   └── admin/
│       └── css/
│           ├── fa-admin.css            # Admin panel RTL (150 KB)
│           └── fa-install.css          # Install page RTL (141 KB)
└── TypeRenew_usr/                      # User theme package
    ├── langs/
    │   ├── fa_IR.mo                    # Persian core language pack
    │   └── en_US.mo                    # English core language pack
    └── themes/
        └── default/
            ├── README.md
            ├── header.php              # Language detection + CSS injection (patched)
            ├── index.php               # Theme metadata header (patched)
            ├── fa-theme.css            # Complete RTL + Vazirmatn font (148 KB)
            ├── style.css               # Original LTR style (unchanged)
            └── langs/
                ├── fa_IR.mo            # Persian theme language pack
                └── en_US.mo            # English theme language pack
```

### 🎯 Features

#### 1. User Theme Package
- **Multi-language:** Persian (fa_IR) + English (en_US) + extensible
- **Auto RTL/LTR:** Server-side detection via PHP
- **Vazirmatn Font:** Embedded (Regular + Bold) in `fa-theme.css`
- **45 Translated Strings:** Complete theme interface translation
- **Persian Numerals:** `font-variant-numeric: persian`
- **Optimized Typography:** `line-height: 1.8` for better Persian readability
- **Dark Mode Support:** Uses TypeRenew CSS variables
- **Responsive:** 768px mobile breakpoint with RTL adjustments

#### 2. Admin Panel Package
- **2 CSS Files Only:** No separate fonts or plugins needed
- **Server-side Detection:** Uses PHP, not JavaScript
- **Update-safe:** Re-add 2 PHP code snippets after updates
- **157 RTL Selectors:** Full admin panel coverage
- **~80 RTL Selectors:** Installation page coverage
- **No Flicker:** `dir="rtl"` applied in `<head>` before body render

### 🚀 Quick Installation

**Theme Installation:**
```bash
# As new theme
cp -r TypeRenew_usr/themes/default /path/to/typerenew/usr/themes/default

# Or replace existing files
cd /path/to/typerenew/usr/themes/default/
cp /path/to/TypeRenew-Add-ons/TypeRenew_usr/themes/default/{header.php,index.php,fa-theme.css} .
cp -r /path/to/TypeRenew-Add-ons/TypeRenew_usr/themes/default/langs .
```

**Admin Installation:**
```bash
# Step 1: Upload CSS files
cp TypeRenew_admin/admin/css/*.css /path/to/typerenew/admin/css/

# Step 2: Patch admin/header.php (see detailed instructions in README)
# Step 3: Patch install.php (see detailed instructions in README)
```

### 📊 Comparison

| Feature | Default TypeRenew | This Package |
|---------|-------------------|--------------|
| Languages | Only Chinese | Chinese + Persian + English (extensible) |
| RTL Support | ❌ No | ✅ Auto (based on active language) |
| Font | System default | Vazirmatn embedded (in RTL mode) |
| Language Files | ❌ None | `.mo` at two levels (theme + core) |
| Admin RTL | ❌ No | ✅ 157 selectors |
| Install RTL | ❌ No | ✅ ~80 selectors |
| Extra Size | — | 291 KB (admin) + 148 KB (theme) |

### 🔧 Technical Details

**RTL Detection Logic:**
```php
// Detects Persian, Arabic, Hebrew, Urdu, Yiddish
$__isRtl = (bool) preg_match('/^(fa|ar|he|ur|yi)([-_][A-Z]{2})?$/i', $__themeLang);
```

**CSS Override Pattern:**
- Theme: Complete replacement (`fa-theme.css` overrides `style.css`)
- Admin: Additive overrides (`html[dir="rtl"]` selectors)

### 📜 License

| Component | License |
|-----------|---------|
| Vazirmatn Font | SIL Open Font License 1.1 |
| CSS/PHP Code | GPL v2 |
| Language Files | GPL v2 |

### ⭐ Compatibility

- **TypeRenew:** v1.5.1+
- **PHP:** 7.4+ and 8.0+
- **Browsers:** Chrome, Firefox, Edge, Safari (recent versions)

### 📝 Changelog

**v1.0.0** (2026-06-27) — Initial Release
- Complete Persian (fa_IR) and English (en_US) language packs
- RTL styling for theme, admin panel, and installation page
- Vazirmatn font embedded in all CSS files
- Auto RTL/LTR switching based on active language

---

## Persian

<h2 id="persian">🇮🇷 راه‌حل کامل RTL/LTR برای TypeRenew</h2>



### 📖 معرفی

این مخزن **پشتیبانی کامل راست‌چین (RTL) و چپ‌چین (LTR)** را به همراه **بسته‌های زبانی فارسی (fa_IR)** و **انگلیسی (en_US)** برای [TypeRenew](https://www.typerenew.com/) نسخه ۱.۵.۱ فراهم می‌کند. یک راه‌حل سبک و بدون افزونه که تمام بخش‌های TypeRenew را برای کاربران فارسی‌زبان بهینه‌سازی می‌کند.

**فلسفه طراحی:**
- ✅ حداقل تغییرات در هسته (فقط ۲ قطعه کد کوچک PHP)
- ✅ بدون وابستگی به منابع خارجی (فونت وزیرمتن به‌صورت base64 در CSS تعبیه شده)
- ✅ تأثیر صفر روی زبان‌های دیگر (CSS فقط در حالت فارسی بارگذاری می‌شود)

### 📁 ساختار مخزن

```
TypeRenew-Add-ons/
├── README.md                           # این فایل
├── TypeRenew_admin/                    # بسته فارسی‌سازی مدیریت
│   ├── README.md
│   └── admin/
│       └── css/
│           ├── fa-admin.css            # RTL پنل مدیریت (۱۵۰ کیلوبایت)
│           └── fa-install.css          # RTL صفحه نصب (۱۴۱ کیلوبایت)
└── TypeRenew_usr/                      # بسته پوسته کاربری
    ├── langs/
    │   ├── fa_IR.mo                    # بسته زبانی فارسی هسته
    │   └── en_US.mo                    # بسته زبانی انگلیسی هسته
    └── themes/
        └── default/
            ├── README.md
            ├── header.php              # تشخیص زبان + تزریق CSS (پچ‌شده)
            ├── index.php               # هدر متادیتای پوسته (پچ‌شده)
            ├── fa-theme.css            # استایل کامل RTL + فونت وزیرمتن (۱۴۸ کیلوبایت)
            ├── style.css               # استایل اصلی LTR (بدون تغییر)
            └── langs/
                ├── fa_IR.mo            # بسته زبانی فارسی پوسته
                └── en_US.mo            # بسته زبانی انگلیسی پوسته
```

### 🎯 ویژگی‌ها

#### ۱. بسته پوسته کاربری
- **چندزبانه:** فارسی (fa_IR) + انگلیسی (en_US) + قابلیت توسعه
- **RTL خودکار:** تشخیص سمت سرور با PHP
- **فونت وزیرمتن:** تعبیه‌شده (Regular + Bold) در `fa-theme.css`
- **۴۵ رشته ترجمه‌شده:** ترجمه کامل رابط پوسته
- **اعداد فارسی:** `font-variant-numeric: persian`
- **تایپوگرافی بهینه:** `line-height: 1.8` برای خوانایی بهتر فارسی
- **پشتیبانی از تم تیره:** استفاده از متغیرهای CSS TypeRenew
- **رسپانسیو:** breakpoint موبایل ۷۶۸px با تنظیمات RTL

#### ۲. بسته پنل مدیریت
- **فقط ۲ فایل CSS:** بدون نیاز به فونت یا پلاگین جداگانه
- **تشخیص سمت سرور:** با PHP، نه جاوااسکریپت
- **پایدار در آپدیت:** فقط ۲ قطعه کد PHP را دوباره اضافه کنید
- **۱۵۷ سلتور RTL:** پوشش کامل پنل مدیریت
- **حدود ۸۰ سلتور RTL:** پوشش صفحه نصب
- **بدون flicker:** `dir="rtl"` در `<head>` قبل از رندر بدنه اعمال می‌شود

### 🚀 نصب سریع

**نصب پوسته:**
```bash
# به‌عنوان پوسته جدید
cp -r TypeRenew_usr/themes/default /path/to/typerenew/usr/themes/default

# یا جایگزینی فایل‌های موجود
cd /path/to/typerenew/usr/themes/default/
cp /path/to/TypeRenew-Add-ons/TypeRenew_usr/themes/default/{header.php,index.php,fa-theme.css} .
cp -r /path/to/TypeRenew-Add-ons/TypeRenew_usr/themes/default/langs .
```

**نصب مدیریت:**
```bash
# گام ۱: آپلود فایل‌های CSS
cp TypeRenew_admin/admin/css/*.css /path/to/typerenew/admin/css/

# گام ۲: پچ admin/header.php (مشاهده دستورالعمل کامل در README)
# گام ۳: پچ install.php (مشاهده دستورالعمل کامل در README)
```

### 📊 مقایسه

| ویژگی | TypeRenew پیش‌فرض | این بسته |
|-------|-------------------|----------|
| زبان‌ها | فقط چینی | چینی + فارسی + انگلیسی (قابل توسعه) |
| پشتیبانی RTL | ❌ ندارد | ✅ خودکار (بر اساس زبان فعال) |
| فونت | سیستم پیش‌فرض | وزیرمتن تعبیه‌شده (در حالت RTL) |
| فایل‌های زبان | ❌ ندارد | `.mo` در دو سطح (پوسته + هسته) |
| RTL مدیریت | ❌ ندارد | ✅ ۱۵۷ سلتور |
| RTL نصب | ❌ ندارد | ✅ حدود ۸۰ سلتور |
| حجم اضافی | — | ۲۹۱ کیلوبایت (مدیریت) + ۱۴۸ کیلوبایت (پوسته) |

### 🔧 جزئیات فنی

**منطق تشخیص RTL:**
```php
// تشخیص فارسی، عربی، عبری، اردو، ییدیش
$__isRtl = (bool) preg_match('/^(fa|ar|he|ur|yi)([-_][A-Z]{2})?$/i', $__themeLang);
```

**الگوی override CSS:**
- پوسته: جایگزینی کامل (`fa-theme.css` روی `style.css` override می‌کند)
- مدیریت: override اضافی (سلتورهای `html[dir="rtl"]`)

### 📜 مجوزها

| بخش | مجوز |
|------|------|
| فونت وزیرمتن | SIL Open Font License 1.1 |
| کد CSS/PHP | GPL v2 |
| فایل‌های زبان | GPL v2 |


### ⭐ سازگاری

- **TypeRenew:** نسخه ۱.۵.۱+
- **PHP:** ۷.۴+ و ۸.۰+
- **مرورگرها:** Chrome, Firefox, Edge, Safari (نسخه‌های اخیر)


### 📝 تاریخچه تغییرات

**نسخه ۱.۰.۰** (۲۰۲۶-۰۶-۲۷) — انتشار اولیه
- بسته‌های زبانی کامل فارسی (fa_IR) و انگلیسی (en_US)
- استایل RTL برای پوسته، پنل مدیریت و صفحه نصب
- فونت وزیرمتن تعبیه‌شده در تمام فایل‌های CSS
- تغییر خودکار RTL/LTR بر اساس زبان فعال

---

<p align="center">
  Made with ❤️ for the Persian-speaking TypeRenew community
</p>

<p align="center">
  <a href="https://github.com/yourusername/TypeRenew-Add-ons/issues">Report Bug</a> •
  <a href="https://github.com/yourusername/TypeRenew-Add-ons/issues">Request Feature</a>
</p>
