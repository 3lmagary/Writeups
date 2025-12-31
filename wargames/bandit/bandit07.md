# حل مستوى Bandit 7
**التاريخ:** 2025-9-15  
**المصدر:** OverTheWire — Bandit  
**المستوى:** 7  
**الملف:** `bandit-7.md`

---

## 🎯 الهدف (Goal)
> Find the password for the next level (bandit8).  
> The password is stored in the file data.txt next to the word millionth.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `grep` - للبحث عن نمط في النص
- `cat` - لعرض محتوى الملف

## 🚀 طريقة الحل (Solution Steps)

### 1. الاتصال بالخادم
```bash
ssh -p 2220 bandit7@bandit.labs.overthewire.org
```
أدخل كلمة مرور المستوى 6: `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

### 2. البحث عن الكلمة
```bash
grep "millionth" data.txt
```

### 3. كلمة المرور المستخرجة
```
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

## 💡 ملاحظات (Notes)
- استخدمنا `grep` للبحث عن نمط نصي في الملف

---
