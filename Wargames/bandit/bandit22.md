# حل Bandit Level 22 → 23

**التاريخ:** 2025-10-27

---

## الوصف

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.


---

## الأوامر اللي استخدمناها
- `cd /etc/cron.d`
- `cat cronjob_bandit23`
- `cat /usr/bin/cronjob_bandit23.sh`
- `echo -n "I am user bandit23" | md5sum | cut -d ' ' -f1`
- `cat /tmp/<hash>`

---

## الحل 
```bash
myname=bandit23; mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1); echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"; cat /etc/bandit_pass/$myname > /tmp/$mytarget

```

### شرح مبسّط لكل جزء
- `myname=bandit23` — يقرأ اسم المستخدم الذي يشغّل السكربت.
- `mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)` — يحسب MD5 للسلسلة "I am user <username>" ليكوّن اسم الملف الهدف في `/tmp`.
- `cat /etc/bandit_pass/$myname > /tmp/$mytarget` — ينسخ كلمة مرور المستخدم إلى ذلك الملف في `/tmp`.



**النتيجة (كلمة مرور bandit23):**
```
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
```
---

لا تنسى الصلاة على النبي محمد ﷺ.

