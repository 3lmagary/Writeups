# حل مستوى Bandit 6
**التاريخ:** 15 - 9 - 2025   
**المصدر:** OverTheWire — Bandit  
**المستوى:** 6  
**الملف:** `bandit-6.md`

---

## 🎯 الهدف (Goal)
> Find the password for the next level (bandit7).  
> The password is stored somewhere on the server and has the following properties:
> - Owned by user bandit7
> - Owned by group bandit6
> - 33 bytes in size

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `find` - للبحث عن الملفات بمواصفات محددة
- `cat` - لعرض محتوى الملف

## 🚀 طريقة الحل (Solution Steps)

### 1. الاتصال بالخادم
```bash
ssh -p 2220 bandit6@bandit.labs.overthewire.org
```
أدخل كلمة مرور المستوى 5: `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

### 2. البحث عن الملف بالمواصفات
```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

### 3. قراءة الملف
```bash
cat /var/lib/dpkg/info/bandit7.password
```

### 4. كلمة المرور المستخرجة
```
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

## 💡 ملاحظات (Notes)
- استخدمنا `2>/dev/null` لتجاهل أخطاء الصلاحيات
- الملف موجود في مسار نظامي

---
