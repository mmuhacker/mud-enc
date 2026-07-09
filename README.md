
<div align="center">

# 🔐 mud-enc | أداة مدارك للتشفير

**أداة سطر أوامر عربية لتشفير وفك تشفير النصوص والأكواد والملفات — بواجهة RTL كاملة**

Arabic-first CLI encryption tool for text, code, and any file type — powered by Fernet (AES-128 + HMAC-SHA256)

[![License](https://img.shields.io/badge/License-No--Derivatives%20Attribution-red)](LICENSE)<br>
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)<br>
[![Platform](https://img.shields.io/badge/Platform-Termux%20%7C%20Linux-green)]()<br>
[![Madarik Tools](https://img.shields.io/badge/Madarik-Tools-orange)](https://github.com/mmuhacker)

</div>

---

## 📖 نبذة

**mud_enc.py** جزء من سلسلة **Madarik Tools (مدارك)** — أداة تشفير عامة تشتغل من الطرفية (Terminal)، وتدعم:

- تشفير وفك تشفير أي **نص أو كود برمجي** يُلصق مباشرة
- تشفير وفك تشفير **أي نوع ملف** (نصوص، صور، APK، أرشيفات، إلخ) دون أي فقدان أو تلف بالبيانات
- **كشف تلقائي**: تلصق نص، والأداة تعرف وحدها إذا لازم تشفّره أو تفك تشفيره
- وضعان لتوليد المفتاح: **كلمة مرور** (PBKDF2 + Salt عشوائي) أو **ملف مفتاح** (`.key`) عشوائي
- تشفير معياري بـ **Fernet (AES-128-CBC + HMAC-SHA256)** من مكتبة `cryptography`
- واجهة عربية **RTL كاملة** مع صناديق وحدود قابلة للتخصيص
- يعمل على **Termux (أندرويد)** و **توزيعات لينكس** بدون أي تعديل

---

## 🖼️ لقطات من الأداة

> *(سيتم إضافة لقطات الشاشة هنا)*

<!--
<p align="center">
  <img src="docs/screenshot-banner.png" width="600" alt="بانر الأداة">
  <img src="docs/screenshot-menu.png" width="600" alt="القائمة الرئيسية">
</p>
-->

---

## ⚙️ التثبيت

### على Termux (أندرويد)

- **الخطوة الأولى:** تحديث النظام والمكتبات

pkg update && pkg install python -y

- **الخطوة الثانية:** تثبيت python-cryptography

  pkg install python-cryptography -y

- **الخطوة الثالثة:** تثبيت المكتبات المطلوبة لعرض النص العربي بالشكل الصحيح

  pip install arabic_reshaper python-bidi==0.4.2

- **الخطوة الرابعة:** تثبيت الأداة

  curl -L -o ~/mud_enc.py https://raw.githubusercontent.com/mmuhacker/mud-enc/main/mud_enc.py
  
- **الخطوة الخامسة:** إعطاء صلاحية التنفيذ
  
  chmod +x ~/mud_enc.py

- **الخطوة السادسة:** إنشاء إختصار التشغيل

  ln -sf ~/mud_enc.py $PREFIX/bin/enc
  
```bash
pkg update && pkg install python -y && pkg install python-cryptography -y && pip install arabic_reshaper python-bidi==0.4.2

curl -L -o ~/mud_enc.py https://raw.githubusercontent.com/mmuhacker/mud-enc/main/mud_enc.py && chmod +x ~/mud_enc.py && ln -sf ~/mud_enc.py $PREFIX/bin/enc
```

بعدها تشغّل الأداة من أي مكان بالأمر:

```bash
enc
```

### على لينكس

```bash
pip install cryptography arabic_reshaper python-bidi==0.4.2 --break-system-packages

curl -L -o ~/mud_enc.py https://raw.githubusercontent.com/mmuhacker/mud-enc/main/mud_enc.py
chmod +x ~/mud_enc.py
sudo ln -sf ~/mud_enc.py /usr/local/bin/enc
```

```bash
enc
```

> إذا واجهت مشكلة باستيراد `cryptography` على Termux (خطأ `dlopen` / ABI)، ثبّتها عن طريق `pkg install python-cryptography` بدل `pip` — نسخة `pkg` مبنية خصيصاً لبيئة Termux.

---

## 🚀 الاستخدام

عند التشغيل، الأداة بتطلب منك:

1. **تخصيص المظهر** (اختياري) — لون الإطار، لون خلفيته، لون النص
2. **طريقة توليد المفتاح** — كلمة مرور، أو ملف مفتاح `.key` (توليد جديد أو تحميل موجود)
3. من القائمة الرئيسية تختار:
   - **تشفير / فك تشفير نص** — تلصق النص مباشرة، والأداة تكتشف تلقائياً إذا يحتاج تشفير أو فك تشفير
   - **تشفير ملف** — تعطيها مسار أي ملف، وبترجعلك نسخة مشفرة بامتداد `.mud`
   - **فك تشفير ملف** — تعطيها ملف `.mud`، وبترجعلك الملف الأصلي كما هو تماماً

بعد كل عملية، فيك تحفظ النتيجة أو تنسخ الملف الناتج مباشرة **لمجلد التنزيلات** (تُكتشف تلقائياً حسب المنصة).

---

## 🎨 التخصيص

كل شاشة بالأداة (البانر، القوائم) مبنية على متغيرات عرض مستقلة لكل سطر، فتقدر تتحكم بعدد أحرف/حشو أي سطر بمفرده مباشرة من الكود، بالإضافة لاتجاه المحاذاة (`rjust` / `ljust` / `center`) ولون الإطار وخلفيته ولون النص بشكل منفصل تماماً عن بعض.

---

## 🔒 كيف يشتغل التشفير

- **وضع كلمة المرور**: يُشتق مفتاح 256-بت عبر `PBKDF2HMAC-SHA256` بـ 200,000 تكرار و Salt عشوائي مختلف بكل عملية — نفس كلمة المرور بترجع نفس الملف الأصلي بالضبط.
- **وضع ملف المفتاح**: مفتاح Fernet عشوائي بالكامل (`Fernet.generate_key()`) يُحفظ بملف `.key` منفصل — أقوى من كلمة المرور، بس لازم تحافظ على الملف نفسه.
- الملفات تُقرأ وتُكتب بصيغة ثنائية (`rb`/`wb`) فتشتغل صح مع أي نوع ملف بدون أي تلف بالبيانات.
- **لا توجد طريقة لاسترجاع البيانات إذا فقدت كلمة المرور أو ملف المفتاح** — هذا تصميم مقصود لضمان الأمان الحقيقي.

---

## 📜 الرخصة

هذا المشروع مرخّص بموجب [رخصة مدارك تولز — النسخ والتوزيع بدون تعديل مع ذكر المصدر](https://github.com/mmuhacker/mud-enc/blob/main/LICENSE.md).

**بالمختصر:**
- ✅ مسموح: نسخ الأداة كاملة غير معدلة، واستخدامها، وإعادة توزيعها، مع ذكر المصدر ورابط المستودع
- ❌ ممنوع: تعديل الكود أو توزيع نسخة معدّلة منه، أو ادعاء ملكيته

راجع ملف [LICENSE](https://github.com/mmuhacker/mud-enc/blob/main/LICENSE.md) للنص الكامل.

---

## 👤 المؤلف

**محند (mmuhacker)** — مطور مستقل، صاحب سلسلة أدوات **Madarik Tools (مدارك)** لأدوات الأمن السيبراني و OSINT العربية.

- GitHub: [@mmuhacker](https://github.com/mmuhacker)

---

<div align="center">

صُنعت بـ 🖤 كجزء من **Madarik Tools**

</div>
