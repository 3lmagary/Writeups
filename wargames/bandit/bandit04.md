# حل مستوى Bandit 4
**التاريخ:** 2025-9-12  
**المصدر:** OverTheWire — Bandit  


---

## 🎯 الهدف (Goal)
> Find the password for the next level (bandit5).  
> The password is stored in the only human-readable file in the inhere directory.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `ls` - لعرض محتويات المجلد
- `file` - للتحقق من نوع الملف
- `cat` - لعرض محتوى الملف

## 🚀 طريقة الحل (Solution Steps)

### 1. الاتصال بالخادم
```bash
ssh -p 2220 bandit4@bandit.labs.overthewire.org
```
أدخل كلمة مرور المستوى 3: `aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG`

### 2. الانتقال إلى المجلد
```bash
cd inhere
```

### 3. فحص أنواع الملفات
```bash
file ./*
```

### 4. البحث عن الملف المقروء
```bash
cat ./-file07
```

### 5. كلمة المرور المستخرجة
```
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```

## 💡 ملاحظات (Notes)
- استخدمنا `file ./*` للتحقق من نوع كل الملفات
- الملف المقروء كان `-file07`

---