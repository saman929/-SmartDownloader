# 📥 SmartDownloader  
سیستمی فوق‌پایدار برای دانلود فایل‌ها از هر نوع لینک—even CDNهای سخت مثل PyTorch، HuggingFace، Google، Firebase و لینک‌های Redirect.

**SmartDownloader** یک GitHub Actions Workflow است که فایل‌ها را:
- کاملاً خودکار دانلود می‌کند  
- فایل خراب یا HTML را تشخیص می‌دهد  
- در صورت نیاز chunk‑download انجام می‌دهد  
- دانلودها را داخل پوشهٔ `downloads/` ذخیره می‌کند  
- و در نهایت commit و push می‌کند  

---

# 🚀 ویژگی‌ها

### ✔ دانلود هوشمند (Smart Engine)
شناساگر خودکار لینک‌ها:
- CDNهای محدود → **curl**
- لینک‌های معمولی → **aria2**

### ✔ جلوگیری از فایل HTML/0KB
اگر فایل:
- HTML باشد  
- خراب باشد  
- 0KB باشد  

سیستم به طور خودکار وارد **chunk mode** می‌شود.

### ✔ دانلود تکه‌تکه (Chunking Mode)
برای سرورهای حساس:
- فایل در قطعات 20MB دانلود می‌شود  
- بعداً دوباره به فایل اصلی تبدیل می‌شود

### ✔ پشتیبانی از Resume
در لینک‌هایی که قطع می‌شوند.

### ✔ retry تا 15 بار  
با backoff تصاعدی.

### ✔ Split خودکار فایل‌های بزرگ
برای سازگاری با GitHub.

### ✔ Commit خودکار  
در دسته‌های ۵تایی برای جلوگیری از conflict.

---

# 📁 ساختار پروژه

```
SmartDownloader
 ├── downloads/
 └── .github/
      └── workflows/
           └── downloader.yaml
```

---

# ▶️ نحوه اجرا

## 1) وارد تب Actions شوید  
در ریپازیتوری خود، به بخش **Actions** بروید.

## 2) Workflow را انتخاب کنید  
Workflow با نام:

```
SmartDownloader - Ultra Mode
```

نمایش داده می‌شود.

## 3) روی **Run workflow** بزنید

## 4) URLها را وارد کنید  
چند لینک را با فاصله جدا کنید، مثال:

```
https://download.pytorch.org/whl/cu118/torch-2.0.1%2Bcu118-cp310-cp310-linux_x86_64.whl https://download.pytorch.org/whl/cu118/torchvision-0.15.2%2Bcu118-cp310-cp310-linux_x86_64.whl
```

## 5) Mode  
- normal → فایل‌ها مستقیم می‌آیند  
- zip → همه در یک ZIP قرار می‌گیرند

## 6) Split  
برای تقسیم فایل‌های بزرگ، مقدار MB مشخص کنید.

---

# 📤 خروجی‌ها

تمام فایل‌های دانلودشده در مسیر زیر قرار می‌گیرند:

```
downloads/
```

و به صورت خودکار commit و push می‌شوند.

---

# 🧠 منطق داخلی SmartDownloader

- تلاش تا 15 بار  
- backoff هوشمند  
- chunk mode خودکار  
- جلوگیری از HTML trap  
- تشخیص فایل‌های خراب  
- بازسازی chunkها  
- split فایل‌های بزرگ  
- commit در batchهای ۵تایی  

---

# 🤝 مشارکت  
Pull Request و Issue پذیرفته می‌شود.

---

# 📄 لایسنس  
MIT License

---
