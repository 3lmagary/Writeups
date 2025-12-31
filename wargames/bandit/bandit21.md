# حل Bandit Level 20 → 21

**التاريخ:** 2025-09-27

---

## الوصف
الهدف: هناك برنامج يعمل تلقائيًا بفواصل زمنية باستخدام `cron` (المُجدول الزمني). اذهب إلى المجلد `/etc/cron.d/` واقرأ تكوينات الـ cron لتعرف أي أمر يتم تنفيذه.

> بالعامية: المطلوب تلاقي ملف الإعداد داخل `/etc/cron.d/` وتشوف أي سكربت أو أمر بيتنفّذ أوتوماتيكيًا — وبالتحديد هنا نبحث عن `cronjob_bandit22`.

---

## الأدوات المستخدمة
- `cd`
- `ls -al`
- `cat`

---

## خطوات الحل (خطوة بخطوة)
1. الانتقال إلى مجلد إعدادات cron:
```bash
cd /etc/cron.d
```

2. عرض محتويات المجلد:
```bash
ls -la
```
**الناتج (مقتطف):**
```
behemoth4_cleanup  clean_tmp  cronjob_bandit22  cronjob_bandit23  cronjob_bandit24  e2scrub_all  leviathan5_cleanup  manpage3_resetpw_job  otw-tmp-dir  sysstat
```

3. عرض محتوى ملف `cronjob_bandit22`:
```bash
cat cronjob_bandit22
```
**الناتج:**
```
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```

### شرح السطور اللي ظهرت
- `@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null`  
  يعني: نفّذ السكربت `/usr/bin/cronjob_bandit22.sh` كـ المستخدم `bandit22` عند كل إعادة تشغيل للنظام. إعادة التوجيه `&> /dev/null` تعني أن مخرجات السكربت (الطبيعية والأخطاء) تُرسل إلى `/dev/null` (أي لا تُعرض).

- `* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null`  
  يعني: نفّذ نفس السكربت **كل دقيقة** كـ `bandit22`. الترتيب هنا في ملفات `/etc/cron.d/` هو: `minute hour day-of-month month day-of-week user command`.

---

4. عرض محتوى السكربت نفسه:
```bash
cat /usr/bin/cronjob_bandit22.sh
```
**الناتج:**
```bash
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

### شرح كل سطر في السكربت
- `#!/bin/bash`  
  تعرّف أن السكربت سيُنفذ باستخدام `bash`.

- `chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`  
  يغيّر أذونات الملف المؤقت في `/tmp` ليصبح قابلاً للقراءة من قبل المستخدمين الآخرين (`rw-r--r--` للمالك، مجموعة وothers قراءة فقط).

- `cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`  
  ينسخ محتوى ملف كلمة المرور الخاص بالمستخدم `bandit22` إلى الملف المؤقت في `/tmp`. لأن السكربت يُشغّل كـ `bandit22`، الملف المؤقت سيحتوي على كلمة المرور وبأذونات تسمح لغيره بقراءته.

---

## كيف تستخرج كلمة المرور بنفسك (باختصار)
بما أن السكربت يكتب كلمة المرور إلى:
```
/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
مع أذونات `644`، يمكنك ببساطة قراءة الملف:
```bash
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

---

## كلمة السر (النتيجة)
```
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```

---
### لا تنسي الصلاه علي النبي محمد ( صلي الله عليه وسلم )
