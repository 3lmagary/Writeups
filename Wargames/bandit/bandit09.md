# حل مستوى Bandit 9
**التاريخ:** 2025-9-15  
**المصدر:** OverTheWire — Bandit  
**المستوى:** 9  
**الملف:** `bandit-9.md`

---

## 🎯 الهدف (Goal)
> Find the password for the next level (bandit10).  
> The password is stored in the file data.txt in one of the few human-readable strings, preceded by several '=' characters.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `strings` - لاستخراج السلاسل النصية من الملف
- `grep` - للبحث عن نمط في النص

## 🚀 طريقة الحل (Solution Steps)

### 1. الاتصال بالخادم
```bash
ssh -p 2220 bandit9@bandit.labs.overthewire.org
```
أدخل كلمة مرور المستوى 8: `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

### 2. استخراج السلاسل النصية والبحث عن النمط
```bash
strings data.txt | grep "==="
```

### 3. كلمة المرور المستخرجة
```
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

## 💡 ملاحظات (Notes)
- `strings` يستخرج فقط السلاسل النصية القابلة للقراءة من الملف
- النمط المستهدف كان محاطًا بعلامات `===`

---
