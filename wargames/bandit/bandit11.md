# حل مستوى Bandit 11
**التاريخ:** 2023-10-15  
**المصدر:** OverTheWire — Bandit  
**المستوى:** 11  
**الملف:** `bandit-11.md`

---

## 🎯 الهدف (Goal)
> Find the password for the next level (bandit12).  
> The password is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `tr` - لترجمة/استبدال الأحرف
- `cat` - لعرض محتوى الملف

## 🚀 طريقة الحل (Solution Steps)

### 1. الاتصال بالخادم
```bash
ssh -p 2220 bandit11@bandit.labs.overthewire.org
```
أدخل كلمة مرور المستوى 10: `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`

### 2. فك تشفير ROT13
```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

### 3. كلمة المرور المستخرجة
```
JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```

## 💡 ملاحظات (Notes)
- ROT13 هو خوارزمية بسيطة لإخفاء النص
- `tr` تقوم بترجمة الأحرف حسب القواعد المحددة

---