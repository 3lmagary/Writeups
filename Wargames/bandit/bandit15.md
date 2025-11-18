# حل Bandit Level 15 → 16

**التاريخ:** 2025-09-20

---

## الخطوات المطلوبة
1. الاتصال بخادم `localhost` على المنفذ `30001` باستخدام OpenSSL.
2. إرسال كلمة مرور المستخدم الحالي (`bandit15`).
3. الحصول على كلمة مرور المستخدم التالي (`bandit16`).

## الحل

### الأمر الكامل
#openssl
```bash
echo "8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo" | openssl s_client -quiet -connect localhost:30001
```

### شرح الحل
1. `echo "8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo"` - يرسل كلمة مرور المستخدم `bandit15`.
2. `openssl s_client -quiet -connect localhost:30001` - ينشئ اتصالًا آمنًا مع الخادم على المنفذ `30001`.
   - `-quiet` - يقلل من الإخراج غير الضروري.
   - `-connect` - يحدد العنوان والمنفذ للاتصال.

### النتيجة المتوقعة
سيتم إرجاع الرد من الخادم والذي يتضمن عادة كلمة مرور المستخدم `bandit16`، مثال خروج متوقع:
```
Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```

## معلومات إضافية
- هذا الاتصال يتطلب استخدام SSL/TLS.
- المنفذ `30001` يستعمل تشفيرًا، لذلك نستخدم `openssl s_client` بدل `nc`.

