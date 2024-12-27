# EDtunnel

<p align="left">
  <img src="https://github.com/user-attachments/assets/f270e6a8-cccb-411f-a0b0-0617a3e25ff4" width="240px" 
   style="margin-bottom: -50px;" alt="https://github.com/NiREvil/Emotional-Damage"<figcaption>
</p>

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)
؛**EDtunnel** یک ابزار برای ساخت پروکسیاز طریق workers و pages کلادفلر است که پشتیبانی از چندین پروتکل و گزینه‌های پیکربندی را ارائه می‌دهد.  
با عرض بینهایت تشکر از [![Github](https://img.shields.io/badge/6KmFi6HP-004953.svg?logo=rockstargames)](https://github.com/6Kmfi6HP)

[![Repository](https://img.shields.io/badge/VIEW_ON-GitHub-blue.svg?logo=github)](https://github.com/NiREvil/Emotional-Damage)
[![Telegram](https://img.shields.io/badge/DISCUSS_ON-TELEGRAM-blue.svg?logo=telegram)](https://t.me/F_NiREvil)
[![Readme](https://img.shields.io/badge/README_IN-فارسی-blue?logo=readme)](README.fa.md)
[![Readme](https://img.shields.io/badge/README_IN-ENGLISH-blue?logo=readme)](README.md)
![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)


## ویژگی‌ها

- پشتیبانی از پیکربندی از طریق workers و pages کلادفلر
- پشتیبانی از چندین UUID همزمان
- پشتیبانی از آدرس پروکسی سفارشی و پورت
- پشتیبانی از پروکسی SOCKS5
- لینک اشتراک (ساب) خودکار
- فرآیند انتشار ساده و آسان

## پیکربندی سریع

### پیکربندی از طریق Pages.dev

1. ویدیو آموزش نحوه ایجاد Cloudflare Pages:
   [![Youtube](https://img.shields.io/badge/YouTube-FE0000?logo=youtube)](https://www.youtube.com/watch?v=8I-yTNHB0aw)

3. دانلود این رپو و جایگذاری در Cloudflare Pages

### پیکربندی از طریق Worker.dev

1. کپی محتویات کد `worker.js_` از [![Here](https://img.shields.io/badge/اینجا-blue?logo=opencollective)](_worker.js)

3. و یا کلیک بر روی دکمه زیر برای دپلوی مستقیم:

   [![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/NiREvil/Emotional-Damage)

## راهنمای پیکربندی

### متغیرهای محیطی

| متغیر | الزامی | مثال | توضیح |
|------------------|-------------------|---------------|-------------------|
| `UUID` | نیست | تک: `12345678-1234-1234-1234-123456789012`<br>چندتایی: `uuid1,uuid2,uuid3` | ای دی شناسایی کاربر<br>برای تولید UUID خودتان به [![UUID](https://img.shields.io/badge/UUID_generator-gray?logo=lucid)](https://www.uuidgenerator.net) مراجعه کنید |
| `PROXYIP` | نیست | `1.1.1.1` یا `example.com`<br>چندتایی: `1.1.1.1:9443,2.2.2.2:8443`<br>برای پیدا کردن آدرس پروکسی آی‌پی به [![ProxyIP](https://img.shields.io/badge/Check_here-gray?logo=envoyproxy)](https://github.com/NiREvil/vless/blob/main/sub/ProxyIP.md) مراجعه کنید | آدرس پروکسی آی‌پی سفارشی و پورت |
| `SOCKS5` | نیست | `user:pass@host:port`<br>چندتایی: `user1:pass1@host1:port1,user2:pass2@host2:port2` | پیکربندی پروکسی SOCKS5 |
| `SOCKS5_RELAY` | نیست | `true` یا `false` | فعال کردن ترافیک پروکسی SOCKS5 |

### پیکربندی پورت غیر 443

1. بازدید از `https://proxyip.edtunnel.best/`
2. ورود به آدرس پروکسی آی‌پی و پورت و کلیک بر روی تست
3. هنگامی که نشان می‌دهد آدرس پروکسی آی‌پی: true، آن موجود است
4. پیکربندی در Worker: `PROXYIP=211.230.110.231:50008`
5. برای پیدا کردن پروکسی آی‌پی به [![ProxyIP](https://img.shields.io/badge/Check_here-gray?logo=envoyproxy)](https://github.com/NiREvil/vless/blob/main/sub/ProxyIP.md) مراجعه کنید

هشدار: آدرس‌های پروکسی آی‌پی با پورت‌ ممکن است در سایت‌های کلادفلر HTTP-only کار نکنند.

### پیکربندی UUID

#### روش 1
در فایل `wrangler.toml` قرار دهید (برای رپو‌های عمومی توصیه نمی‌شود)

```toml
[vars]
UUID = "your-uuid-here"
```

#### روش 2
در داشبورد کلادفلر متغیرهای محیطی قرار دهید (روش توصیه شده)

## هشدار مهم: جداکننده پیکربندی چندگانه

تمامی پیکربندی‌های چندگانه باید از جداکننده انگلیسی کاما (،) استفاده کنند، نه جداکننده چینی کاما (،)

✅ نمونه‌های درست:
```bash
# چند UUID
UUID=uuid1,uuid2,uuid3

# چند پروکسی SOCKS5
SOCKS5=192.168.1.1:1080,192.168.1.2:1080

# چند آدرس پروکسی
PROXYIP=1.1.1.1:443,2.2.2.2:443
```

❌ نمونه‌های نادرست:
```bash
# نادرست: استفاده از جداکننده چینی کاما
UUID=uuid1，uuid2，uuid3

# نادرست: استفاده از جداکننده چینی کاما
SOCKS5=192.168.1.1:1080，192.168.1.2:1080
```

## شروع سریع

### اشتراک پیکربندی خودکار

برای اشتراک پیکربندی خودکار از لینک زیر استفاده کنید:
```
https://sub.xf.free.hr/auto
```

### نمایش پیکربندی

- بازدید از دامنه: `https://your-domain.pages.dev`
- استفاده از UUID خود: `/sub/[uuid]`
- نمایش پیکربندی کامل: بازدید از مسیر ریشه دامنه
- دریافت محتوا اشتراک: بازدید از `/sub/[uuid]`

## پیکربندی پیشرفته

### پشتیبانی از چند UUID

می‌توانید پیکربندی چند UUID را در این روش‌ها انجام دهید:

1. از طریق متغیرهای محیطی:
   ```
   UUID=uuid1,uuid2,uuid3
   ```

2. از طریق فایل پیکربندی:
   ```toml
   [vars]
   UUID = "uuid1,uuid2,uuid3"
   ```

### پیکربندی پروکسی SOCKS5

پشتیبانی از فرمت‌های زیر را ارائه می‌دهد:
- فرمت اساسی: `host:port`
- فرمت احراز هویت: `username:password@host:port`
- چند پروکسی (با جداکننده انگلیسی کاما): `proxy1,proxy2,proxy3`

#### نمونه‌های پیکربندی:

1. پروکسی تکی:
```bash
# فرمت اساسی
SOCKS5=192.168.1.1:1080

# با احراز هویت
SOCKS5=user:pass@192.168.1.1:1080
```

2. چند پروکسی (با جداکننده انگلیسی کاما):
```bash
# چند پروکسی اساسی
SOCKS5=192.168.1.1:1080,192.168.1.2:1080,192.168.1.3:1080

# چند پروکسی با احراز هویت
SOCKS5=user1:pass1@host1:port1,user2:pass2@host2:port2

# فرمت مخلوط
SOCKS5=192.168.1.1:1080,user:pass@192.168.1.2:1080,192.168.1.3:1080
```

#### بارگذاری مجدد پروکسی SOCKS5

هنگامی که چند پروکسی پیکربندی شده است، سیستم بارگذاری مجدد را انجام می‌دهد:

- انتخاب تصادفی
- بارگذاری مجدد اتوماتیک
- پشتیبانی از روش‌های احراز هویت مخلوط

#### پیکربندی SOCKS5_RELAY

فعال سازی انتقال پروکسی SOCKS5:
```bash
SOCKS5_RELAY=true
```

#### توجه
- اطمینان حاصل کنید که سرورهای پروکسی پیکربندی شده پایدار و دسترسی پذیر هستند
- پیشنهاد می شود از پروکسی های خصوصی برای امنیت بیشتر استفاده کنید
- از کاما برای جداسازی پروکسی های چندگانه استفاده کنید
- پشتیبانی از افزودن و حذف پروکسی های پویا

## 🚨 توجه

 پروکسی آی‌پی های با پورت در سایت های HTTP فقط Cloudflare کار نمی کنند
- از کاما برای جداسازی UUID های چندگانه استفاده کنید
- پیشنهاد می شود اطلاعات را از طریق متغیرهای محیطی تنظیم کنید
- برای دریافت آخرین ویژگی ها و به روز رسانی های امنیتی، به روز رسانی های منظم را انجام دهید.


## 🔧 پیکربندی متغیرهای محیطی

### پیکربندی از طریق Workers.dev

**متغیرهای محیطی در Workers.dev**
![Workers](https://github.com/user-attachments/assets/77db9a1d-7f57-48f5-91d8-9c9b2c7f78c3)


### پیکربندی از طریق pages.dev

**متغیرهای محیطی در Pages.dev**
![Pages](https://github.com/user-attachments/assets/9a425287-1efc-4a3f-8c3a-6ca8a9214a1e)


## 💬 ارائه کمک یا پیشنهاد

- گروه تلگرام: [گروه NiREvil](https://t.me/NiREvil_GP)
- مخزن گیت‌هاب: [Emotional-Damage](https://github.com/NiREvil/Emotional-Damage)
- گزارش مشکل: [گزارش مشکل جدید](https://github.com/NiREvil/Emotional-Damage/issues)


## 📝 مشارکت

**خوش آمدید برای ثبت درخواست هایی که پروژه را بهبود می بخشند! لطفا تضمین کنید:**
1. کد بر اساس استانداردهای پروژه نوشته شده است
2. آزمون های مربوطه را افزوده اید
3. مستندات مربوطه را به روز کرده اید
4. دلایل تغییرات را به طور مشخص توضیح دهید.
