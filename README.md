
<div align="center">

# 🔐 mud-enc | أداة مدارك للتشفير

**أداة سطر أوامر عربية لتشفير وفك تشفير النصوص والأكواد والملفات — بواجهة RTL كاملة**

Arabic-first CLI encryption tool for text, code, and any file type — powered by Fernet (AES-128 + HMAC-SHA256)

[![License](https://img.shields.io/badge/License-No--Derivatives%20Attribution-red)](LICENSE)<br>
![License](https://img.shields.io/badge/%EF%BA%97%EF%BA%AE%EF%BA%A7%EF%BB%B4%EF%BA%BA%20%EF%BA%A7%EF%BA%8E%D8%B5-%EF%BA%8D%EF%BB%9F%EF%BA%98%EF%BA%AE%EF%BA%A7%EF%BB%B4%EF%BA%BA-8A2BE2?style=for-the-badge&logo=law)<br>
[![by](https://img.shields.io/badge/mmuhacker-%EF%BA%97%EF%BB%84%EF%BB%AE%EF%BB%B3%EF%BA%AE-blue?style=for-the-badge&logo=github)](https://github.com/mmuhacker)<br>
![Version](https://img.shields.io/badge/1.0-%EF%BA%8D%EF%BB%B9%EF%BA%BB%EF%BA%AA%EF%BA%8D%EF%BA%AE-blue?style=for-the-badge&logo=semver)<br>
![Platform](https://img.shields.io/badge/%EF%BB%9B%EF%BA%8E%EF%BB%9F%EF%BB%B2%20%EF%BB%9F%EF%BB%B4%EF%BB%A8%EF%BB%9C%EF%BA%B2-%EF%BA%8D%EF%BB%9F%EF%BA%92%EF%BB%B4%EF%BA%8C%EF%BA%94-green?style=for-the-badge&logo=kalilinux&logoColor=%23FFC107)<br>
![Platform](https://img.shields.io/badge/%EF%BA%84%EF%BB%A7%EF%BA%AA%EF%BA%AE%EF%BB%AE%EF%BB%B3%EF%BA%AA-%EF%BA%8D%EF%BB%9F%EF%BA%92%EF%BB%B4%EF%BA%8C%EF%BA%94-green?style=for-the-badge&logo=android)<br>
![Python](https://img.shields.io/badge/3.x-%EF%BA%91%EF%BA%8E%EF%BB%B3%EF%BA%9C%EF%BB%AE%EF%BB%A6-blue?style=for-the-badge&logo=python)<br>
![Status](https://img.shields.io/badge/%EF%BB%A7%EF%BA%B8%EF%BB%82-%EF%BA%8D%EF%BB%9F%EF%BA%A4%EF%BA%8E%EF%BB%9F%EF%BA%94-blue?style=for-the-badge&logo=statuspal)<br>
[![Madarik Tools](https://img.shields.io/badge/Madarik-Tools-orange)](https://github.com/mmuhacker)

</div>

---

📚 ***المحتويات***
- [نبذة عن الأداة](#نبذة)
- [مميزات الأداة](#مميزات)
- [لقطات الأداة](#لقطات)
- **التثبيت**
  - [على Termux 📲](#تيرمكس)
  - [على توزيعات لينكس](#لينكس)
- [المشاكل وحلولها](#error)
- [كيف يعمل التشفير](#كيف)
- [ملف requirements](#txt)
- [🤝 المساهمة](#مساهم)
- [المطور](#المطور)
- [الرخصة License](#رخصة)

---

<div align="center" id="نبذة">
  
## 📖 نبذة عن الأداة
</div>

هي جزء من سلسلة **Madarik Tools (مدارك)** — أداة تشفير عامة تشتغل من الطرفية (Terminal)،

---

<div align="center" id="مميزات">
  
## 🎯 مميزات الأداة
  
</div>

- تخصيص واجهة الأداة عند تشغيل الأداة تستطيع تخصيص ألوان **البانر** و**الخطوط** وإختيار **لون للخلفة** والتحكم بها من داخل الأداة.
- تشفير وفك تشفير أي **نص أو كود برمجي** يُلصق مباشرة
- تشفير وفك تشفير **أي نوع ملف** (نصوص، صور، APK، أرشيفات، إلخ) دون أي فقدان أو تلف بالبيانات
- **كشف تلقائي**: تلصق نص، والأداة تعرف وحدها إذا لازم تشفّره أو تفك تشفيره
- وضعان لتوليد المفتاح: **كلمة مرور** (PBKDF2 + Salt عشوائي) أو **ملف مفتاح** (`.key`) عشوائي
- تشفير معياري بـ **Fernet (AES-128-CBC + HMAC-SHA256)** من مكتبة `cryptography`
- واجهة عربية **RTL كاملة** مع صناديق وحدود قابلة للتخصيص
- يعمل على **Termux (أندرويد)** و **توزيعات لينكس** بدون أي تعديل

---

<div align="center" id="لقطات">

## 🖼️ لقطات من الأداة
</div>

> *(سيتم إضافة لقطات الشاشة هنا)*


<p align="center">
  <img src="img/enc_0.jpg" width="600" alt="بانر الأداة"><br>
  <img src="img/enc_3.jpg" width="600" alt="القائمة الرئيسية">
</p>
-->

---

## ⚙️ التثبيت

<div align="center" id="تيرمكس">

### على Termux (أندرويد)

</div>

- **الخطوة الأولى:** تحديث النظام والمكتبات

```bash
pkg update && pkg install python -y
```

- **الخطوة الثانية:** تثبيت python-cryptography

```bash
pkg install python-cryptography -y
```

- **الخطوة الثالثة:** تثبيت المكتبات المطلوبة لعرض النص العربي بالشكل الصحيح

```bash
pip install arabic_reshaper python-bidi==0.4.2
```

- **الخطوة الرابعة:** تثبيت الخط العربي (للعرض الصحيح)

```bash
curl -L "https://fonts.gstatic.com/s/notonaskharabic/v33/RrQ5bpV-9Dd1b1OAGA6M9PkyDuVBePeKNaxcsss0Y7bwvc-VaA.ttf" -o ~/.termux/font.ttf
termux-reload-settings
```
⚠️ **هام: أغلق Termux تماماً من قائمة التطبيقات الخلفية وافتحه من جديد**

- **الخطوة الخامسة:** تثبيت الأداة
```bash
curl -L -o ~/mud_enc.py https://raw.githubusercontent.com/mmuhacker/mud-enc/main/mud_enc.py
```

- **الخطوة السادسة:** إعطاء صلاحية التنفيذ

```bash
chmod +x ~/mud_enc.py
```
- **الخطوة السابعة:** إنشاء إختصار التشغيل

```bash
ln -sf ~/mud_enc.py $PREFIX/bin/enc
```
  **أو قم بكل شيء بالأمر المُجَمَّع:**
  
```bash
pkg update && pkg install python -y && pkg install python-cryptography -y && pip install arabic_reshaper python-bidi==0.4.2 && curl -L "https://fonts.gstatic.com/s/notonaskharabic/v33/RrQ5bpV-9Dd1b1OAGA6M9PkyDuVBePeKNaxcsss0Y7bwvc-VaA.ttf" -o ~/.termux/font.ttf && termux-reload-settings && curl -L -o ~/mud_enc.py https://raw.githubusercontent.com/mmuhacker/mud-enc/main/mud_enc.py && chmod +x ~/mud_enc.py && ln -sf ~/mud_enc.py $PREFIX/bin/enc
```

**بعدها تشغّل الأداة من أي مكان بالأمر:**

```bash
enc
```
---
<div align="center" id="لينكس">

### على لينكس
</div>

- **الخطوة الأولى:** تحديث النظام

```bash
sudo apt update && sudo apt upgrade -y
```
- **الخطوة الثانية:** تثبيت بايثون إذا لم تكن مثبتة
```bash

```
- **الخطوة الثالثة:** تثبيت cryptography والمكتبات

```bash
pip install cryptography arabic_reshaper python-bidi==0.4.2 --break-system-packages
```

- **الخطوة الرابعة:** تثبيت الأداة وإعطاء صلاحية التنفيذ
```bash
curl -L -o ~/mud_enc.py https://raw.githubusercontent.com/mmuhacker/mud-enc/main/mud_enc.py && chmod +x ~/mud_enc.py
```
- **الخطوة الخامسة:** إنشاء الإختصار **enc**
```bash
sudo ln -sf ~/mud_enc.py /usr/local/bin/enc
```
- **أو قم بعمل كل شيء بالأمر المُجَمَّع:**
```bash
pip install cryptography arabic_reshaper python-bidi==0.4.2 --break-system-packages

curl -L -o ~/mud_enc.py https://raw.githubusercontent.com/mmuhacker/mud-enc/main/mud_enc.py
chmod +x ~/mud_enc.py
sudo ln -sf ~/mud_enc.py /usr/local/bin/enc
```

```bash
enc
```

---
<div align="center" id="error">

## المشاكل وحلولها
</div>

*قد تواجه بعض المشكلات في عمل الأداة وهذه طرق إصلاحها*

> إذا واجهت مشكلة باستيراد `cryptography` على Termux (خطأ `dlopen` / ABI)، ثبّتها عن طريق `pkg install python-cryptography` بدل `pip` — نسخة `pkg` مبنية خصيصاً لبيئة Termux.

---

<div align="center" id="إستخدام">
  
## 🚀 الاستخدام
</div>

عند التشغيل، الأداة بتطلب منك:

1. **تخصيص المظهر** (اختياري) — لون **الإطار**، لون **خلفيته**، لون **النص**.
2. **طريقة توليد المفتاح** — كلمة مرور، أو ملف مفتاح `.key` (توليد جديد أو تحميل موجود)
3. من القائمة الرئيسية تختار:
   - **تشفير / فك تشفير نص** — تلصق النص مباشرة، والأداة تكتشف تلقائياً إذا يحتاج تشفير أو فك تشفير
   - **تشفير ملف** — تعطيها مسار أي ملف، وستعطيك نسخة مشفرة بامتداد `.mud`
   - **فك تشفير ملف** — تعطيها ملف `.mud`، وستعيد الملف الأصلي كما هو تماماً

بعد كل عملية، تستطيع أن تحفظ النتيجة أو تنسخ الملف الناتج مباشرة **لمجلد التنزيلات** (يتم إكتشافه تلقائياً حسب المنصة).

---

<div align="center" id="كيف">
  
## 🔒 كيف يعمل التشفير

</div>

- **وضع كلمة المرور**: يُشتق مفتاح 256-بت عبر `PBKDF2HMAC-SHA256` بـ 200,000 تكرار و Salt عشوائي مختلف بكل عملية — نفس كلمة المرور بترجع نفس الملف الأصلي بالضبط.
- **وضع ملف المفتاح**: مفتاح Fernet عشوائي بالكامل (`Fernet.generate_key()`) يُحفظ بملف `.key` منفصل — أقوى من كلمة المرور، بس لازم تحافظ على الملف نفسه.
- الملفات تُقرأ وتُكتب بصيغة ثنائية (`rb`/`wb`) فتشتغل صح مع أي نوع ملف بدون أي تلف بالبيانات.
- **لا توجد طريقة لاسترجاع البيانات إذا فقدت كلمة المرور أو ملف المفتاح** — هذا تصميم مقصود لضمان الأمان الحقيقي.

---

<div align="center" id="txt">

## 📝 ملف requirements.txt

```
cryptography 
arabic-reshaper&gt;=3.0.0
python-bidi&gt;=0.4.2 x
```

</div>

---

<div align="center" id="مساهم">

## 🤝 المساهمة

</div>

المساهمات مرحب بها! يمكنك:
- فتح Issue للإبلاغ عن خطأ
- تقديم Pull Request لإضافة ميزة
- اقتراح تحسينات عبر Issues

---

<div align="center" id="المطور">

## 👨‍💻 المطور

**Muhannad Daher**

[![GitHub](https://img.shields.io/badge/GitHub-mmuhacker-black?style=for-the-badge&logo=github)](https://github.com/mmuhacker)

</div>

---

<div align="center" id="رخصة">
  
## 📜 الرخصة

</div>

هذا المشروع مرخّص بموجب [رخصة مدارك تولز — النسخ والتوزيع بدون تعديل مع ذكر المصدر](https://github.com/mmuhacker/mud-enc/blob/main/LICENSE.md).

**بالمختصر:**
- ✅ مسموح: نسخ الأداة كاملة غير معدلة، واستخدامها، وإعادة توزيعها، مع ذكر المصدر ورابط المستودع
- ❌ ممنوع: تعديل الكود أو توزيع نسخة معدّلة منه، أو ادعاء ملكيته

راجع ملف [LICENSE](https://github.com/mmuhacker/mud-enc/blob/main/LICENSE.md) للنص الكامل.

---

<div align="center">

صُنعت بـ 🖤 كجزء من **Madarik Tools**

</div>
