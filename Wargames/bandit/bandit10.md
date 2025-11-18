# حل مستوى Bandit 10
**التاريخ:** 2025-9-15  
**المصدر:** OverTheWire — Bandit  
**المستوى:** 10  
**الملف:** `bandit-10.md`

---

## 🎯 الهدف (Goal)
> Find the password for the next level (bandit11).  
> The password is stored in the file data.txt, which contains base64 encoded data.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `base64` - لفك تشفير البيانات
- `cat` - لعرض محتوى الملف

## 🚀 طريقة الحل (Solution Steps)

### 1. الاتصال بالخادم
```bash
ssh -p 2220 bandit10@bandit.labs.overthewire.org
```
أدخل كلمة مرور المستوى 9: `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`

### 2. فك تشفير البيانات
```bash
base64 -d data.txt
```

### 3. كلمة المرور المستخرجة
```
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

## 💡 ملاحظات (Notes)
- `base64 -d` يفك تشفير البيانات المشفرة بتنسيق base64

---
