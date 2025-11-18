# حل مستوى Bandit 2
**التاريخ:** 2025-9-12  
**المصدر:** OverTheWire — Bandit  


---

## 🎯 الهدف (Goal)
> Find the password for the next level (bandit3).  
> The password is stored in a file called "spaces in this filename" located in the home directory.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `ls` - لعرض محتويات المجلد
- `cat` - لعرض محتوى الملف

## 🚀 طريقة الحل (Solution Steps)

### 1. الاتصال بالخادم
```bash
ssh -p 2220 bandit2@bandit.labs.overthewire.org
```
أدخل كلمة مرور المستوى 1: `NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL`

### 2. عرض الملفات
```bash
ls -la
```

### 3. قراءة الملف الذي يحتوي على مسافات
```bash
cat "spaces in this filename"
```

### 4. كلمة المرور المستخرجة
```
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```

## 💡 ملاحظات (Notes)
- نستخدم علامات الاقتباس للتعامل مع الملفات التي تحتوي على مسافات

---