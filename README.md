# پوشش‌نما

نرم‌افزار فارسی تحلیل فایل‌های اکسل آمار تأمین اجتماعی و ساخت گزارش‌های
جمعیت تحت پوشش، بیمه‌شدگان، مستمری‌بگیران، کارگاه‌ها و درمان.

## قابلیت‌ها

- ورود یک فایل جامع چندشیتی یا چند فایل اکسل مستقل
- تشخیص ۱۱ شیت مرجع و ساخت ۱۷ گزارش
- داشبورد ملی با دسترسی مرحله‌ای به جزئیات
- جدول‌های مرتب‌شونده، صفحه‌بندی و خروجی CSV
- رابط راست‌به‌چپ و واکنش‌گرا با فونت Vazirmatn
- ویدیوی سبک کارت جمعیت با بارگذاری تنبل و توقف خارج از دید
- تاریخچه نسخه‌ها در Cloudflare D1
- صفحه عمومی و فقط‌خواندنی مدیریت نسخه‌ها
- ثبت و ویرایش نسخه فقط برای حساب مدیر
- خروجی HTML تک‌فایل برای اجرای آفلاین و GitHub Pages

## اجرای محلی

نیازمندی: Node.js نسخه 22.13 یا جدیدتر.

```bash
npm install
npm run dev
```

ساخت و آزمون:

```bash
npm test
```

ساخت HTML تک‌فایل:

```bash
npx vite build --config work/static-site/vite.config.mjs
npx vite build --config work/static-admin/vite.config.mjs
```

خروجی برنامه در `work/static-dist/index.html` و خروجی مدیریت عمومی در
`work/static-admin-dist/index.html` ساخته می‌شود.

## نسخه‌های آنلاین

- [برنامه عمومی](https://mnikoie2005-cmd.github.io/pooshesh-nama/)
- [مدیریت عمومی فقط‌خواندنی](https://mnikoie2005-cmd.github.io/pooshesh-nama/admin.html)
- [مدیریت خصوصی](https://pooshesh-nama.m-nikoie2005.chatgpt.site/admin)

## ساختار اصلی

- `app/page.tsx`: رابط اصلی، تنظیمات و گزارش‌ها
- `app/report-engine.ts`: موتور محاسبه گزارش‌ها
- `app/admin`: نمایش و مدیریت تاریخچه نسخه‌ها
- `app/public-admin.tsx`: مدیریت عمومی فقط‌خواندنی
- `app/api/versions`: API نسخه‌ها
- `db`: مدل و دسترسی Cloudflare D1
- `drizzle`: مهاجرت‌های دیتابیس
- `work/static-site`: سازنده نسخه تک‌فایل

فایل‌های اکسل در مرورگر کاربر پردازش می‌شوند و برای ساخت گزارش به سرور ارسال
نمی‌شوند. فقط تاریخچه نسخه‌های نرم‌افزار در D1 ذخیره می‌شود.
