<div align="center">

# راست‌چین‌ساز هوش مصنوعی + شمارشگر توکن
### AI RTL Fixer + Token Usage Counter

**[🇮🇷 فارسی](#فارسی) | [🇬🇧 English](#english)**

</div>

---

<a name="فارسی"></a>
## 🇮🇷 فارسی

افزونه‌ی مرورگر (فایرفاکس و کروم) که صفحات چت‌بات‌های معروف هوش مصنوعی — Claude، ChatGPT، Gemini، Grok، Perplexity، Copilot، Poe، HuggingChat، Character.AI، DeepSeek، Le Chat و... — را به‌صورت خودکار **راست‌چین** می‌کند و **تخمین مصرف توکن روزانه و هفتگی** را نمایش می‌دهد.

### ✨ قابلیت‌ها
- راست‌چین خودکار صفحات هوش مصنوعی، با ایزوله ماندن بلوک‌های کد (چپ‌چین باقی می‌مانند)
- سوییچ کلی روشن/خاموش + سوییچ جداگانه برای هر سایت
- امکان افزودن **سایت دلخواه** با اسم و آدرس، بدون نیاز به ویرایش کد یا نصب مجدد
- نمایش تخمین مصرف توکن به‌تفکیک هر سرویس، در دو تب «امروز» و «هفته اخیر»
- کاملاً محلی — هیچ داده‌ای به سروری ارسال نمی‌شود؛ همه‌چیز در `storage.local` خود مرورگر ذخیره می‌شود

### ⚠️ محدودیت مهم درباره‌ی شمارش توکن
هیچ‌کدام از این پلتفرم‌ها عدد دقیق توکن مصرفی را در صفحه نشان نمی‌دهند (این داده فقط سمت سرور آن‌ها موجود است). عدد نمایش‌داده‌شده صرفاً یک **تخمین** بر اساس تعداد کاراکترهای متن رد و بدل شده در صفحه است (تقریب رایج: هر ۴ کاراکتر ≈ ۱ توکن).

### 📦 نصب برای توسعه/تست محلی

**فایرفاکس:**
1. آدرس `about:debugging#/runtime/this-firefox` را باز کنید
2. روی «Load Temporary Add-on» کلیک کنید
3. فایل `manifest.json` داخل پوشه‌ی افزونه را انتخاب کنید

**کروم:**
1. آدرس `chrome://extensions` را باز کنید
2. «حالت توسعه‌دهنده» (Developer mode) را فعال کنید
3. روی «Load unpacked» کلیک کرده و پوشه‌ی افزونه را انتخاب کنید

### 🚀 راهنمای انتشار
راهنمای کامل قدم‌به‌قدم انتشار روی فروشگاه فایرفاکس (AMO) و فروشگاه کروم در فایل [`PUBLISHING.md`](./PUBLISHING.md) آمده است.

### 🗂 ساختار پروژه
```
manifest.json     تنظیمات اصلی افزونه (سازگار با MV3، هم فایرفاکس هم کروم)
background.js     ذخیره‌سازی آمار توکن + ثبت پویای اسکریپت برای سایت‌های دلخواه
content.js        راست‌چین‌سازی صفحه + ایزوله کردن کد + شمارش توکن
rtl.css           استایل‌های راست‌چین و ایزوله‌سازی بلوک کد
popup.html/js/css رابط کاربری آیکون افزونه
_locales/fa       رشته‌های نام و توضیحات افزونه
```

### 🤝 مشارکت
اگر می‌خواهید سایت جدیدی به‌صورت دائمی (نه فقط برای خودتان) به لیست پیش‌فرض اضافه شود، در `content.js` تابع `builtInSiteKey()`، در `popup.js` آبجکت `SITE_LABELS`، و در `manifest.json` آرایه‌های `host_permissions`/`matches` را به‌روزرسانی کنید.

### 📄 مجوز
MIT — آزاد برای استفاده، تغییر و توزیع.

---

<a name="english"></a>
## 🇬🇧 English

A browser extension (Firefox & Chrome) that automatically switches popular AI chat websites — Claude, ChatGPT, Gemini, Grok, Perplexity, Copilot, Poe, HuggingChat, Character.AI, DeepSeek, Le Chat and more — to **right-to-left (RTL)** layout, and shows an **estimated daily/weekly token usage** breakdown per site.

### ✨ Features
- Automatic RTL layout for AI chat sites, while code blocks stay properly isolated in LTR
- Global on/off switch, plus a per-site toggle
- Add **any custom site** by name and URL, no code editing or reinstall needed
- Token usage estimate broken down per site, in "Today" and "Last 7 days" tabs
- Fully local — no data is ever sent to any server; everything lives in the browser's `storage.local`

### ⚠️ Important note on token counting
None of these platforms expose the exact token count on the page itself (that data only exists on their servers). The number shown is a rough **estimate** based on the amount of text rendered on the page (common heuristic: ~4 characters ≈ 1 token).

### 📦 Local install for development/testing

**Firefox:**
1. Open `about:debugging#/runtime/this-firefox`
2. Click "Load Temporary Add-on"
3. Select the `manifest.json` file inside the extension folder

**Chrome:**
1. Open `chrome://extensions`
2. Enable "Developer mode"
3. Click "Load unpacked" and select the extension folder

### 🚀 Publishing guide
See [`PUBLISHING.md`](./PUBLISHING.md) for the full step-by-step guide to publishing on the Firefox Add-ons store (AMO) and the Chrome Web Store.

### 🗂 Project structure
```
manifest.json     Core extension config (MV3, works on both Firefox and Chrome)
background.js     Token usage storage + dynamic content-script registration for custom sites
content.js        Applies RTL, isolates code blocks, tracks token usage
rtl.css           RTL styling and code-block isolation rules
popup.html/js/css Extension toolbar popup UI
_locales/fa       Extension name/description localization strings
```

### 🤝 Contributing
To permanently add a new site to the default list (not just for yourself), update `builtInSiteKey()` in `content.js`, the `SITE_LABELS` object in `popup.js`, and the `host_permissions`/`matches` arrays in `manifest.json`.

### 📄 License
MIT — free to use, modify, and distribute.
