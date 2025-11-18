# حل مستوى Bandit 13 → Bandit 14

**التاريخ:** 2025-9-18  
**المصدر:** OverTheWire — Bandit

---

## 🎯 الهدف (Goal)
> The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user `bandit14`. For this level, you don't get the next password, but you get a private SSH key that can be used to log into the next level. Note: `localhost` is a hostname that refers to the machine you are working on.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم باستخدام مفتاح SSH الخاص.
- `cat` - لعرض محتويات الملفات بعد الدخول (داخل بيئة الاختبار فقط).

## 🚀 طريقة الحل (Solution Steps)

### 1. الاتصال بالمستوى الحالي (Bandit 13)
```bash
ssh -p 2220 bandit13@bandit.labs.overthewire.org
```
أدخل كلمة المرور الخاصة بالمستوى 13.

### 2. عرض محتويات المجلد
```bash
ls -la
```
ستجد ملف `sshkey.private` وهو المفتاح الخاص للاتصال بالمستوى 14.

### 3. استخدام المفتاح الخاص للاتصال بالمستوى 14
#ssh
```bash
ssh -i sshkey.private bandit14@localhost -p 2220
```
### شرح الأمر:

- ssh : أداة الاتصال بـ SSH.

- -i sshkey.private : استخدام المفتاح الخاص بدل كلمة المرور.

- bandit14@localhost : المستخدم bandit14 على نفس الجهاز (localhost).

- -p 2220 : تحديد البورت المخصص للاتصال بهذا المستوى.

### 4. قراءة كلمة مرور المستوى 14
بعد الاتصال كمستخدم `bandit14`, يمكنك قراءة كلمة المرور الخاصة بالمستوى التالي من الملف:
```bash
cat /etc/bandit_pass/bandit14
```

