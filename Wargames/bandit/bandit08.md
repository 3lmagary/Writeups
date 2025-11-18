 مستوى Bandit 8
**التاريخ:** 2025-9-15  
**المصدر:** OverTheWire — Bandit  
**المستوى:** 8  
**الملف:** `bandit-8.md`

---

## 🎯 الهدف (Goal)
> Find the password for the next level (bandit9).  
> The password is stored in the file data.txt and is the only line of text that occurs only once.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `sort` - لترتيب البيانات
- `uniq` - للعثور على الخطوط الفريدة

## 🚀 طريقة الحل (Solution Steps)

### 1. الاتصال بالخادم
```bash
ssh -p 2220 bandit8@bandit.labs.overthewire.org
```
أدخل كلمة مرور المستوى 7: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

### 2. البحث عن الخط الفريد
```bash
sort data.txt | uniq -u
```

### 3. كلمة المرور المستخرجة
```
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

## 💡 ملاحظات (Notes)
- `sort` يرتب البيانات ليعمل `uniq` بشكل صحيح
- `uniq -u` يعرض فقط الخطوط الفريدة التي لا تتكرر

---
