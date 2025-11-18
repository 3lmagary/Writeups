# حل مستوى Bandit 5
**التاريخ:** 2025-9-12  
**المصدر:** OverTheWire — Bandit  


---

## 🎯 الهدف (Goal)
> Find the password for the next level (bandit6).  
> The password is hidden in a file somewhere under the inhere directory with specific properties.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `find` - للبحث عن الملفات بمواصفات محددة
- `cat` - لعرض محتوى الملف

## 🚀 طريقة الحل (Solution Steps)

### 1. الاتصال بالخادم
```bash
ssh -p 2220 bandit5@bandit.labs.overthewire.org
```
أدخل كلمة مرور المستوى 4: `lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR`

### 2. البحث عن الملف بالمواصفات
```bash
find inhere -type f -size 1033c ! -executable
```

### 3. قراءة الملف
```bash
cat inhere/maybehere07/.file2
```

### 4. كلمة المرور المستخرجة
```
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```

## 💡 ملاحظات (Notes)
- استخدمنا `find` مع خيارات محددة للعثور على الملف

---