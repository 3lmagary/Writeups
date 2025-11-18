# حل مستوى Bandit 29 → 30

**التاريخ:** 2025-10-19
**المصدر:** OverTheWire — Bandit
#grep #git 

---

## 🎯 الهدف (Goal)

استنساخ مستودع `git` للمستخدم `bandit29-git` والبحث في تاريخ المستودع (commits/branches/objects) لاستخراج كلمة المرور الخاصة بالمستوى التالي `bandit30`.

---

# الطرق المستخدمة لاستخراج الباسورد 

### فحص سجلّ الكوميتات والملف نفسه (Commit history)

**فكرة:** غالبًا يُضاف الباسورد داخل ملف (مثل `README.md`) في مرحلة ما ثم يُعدّل أو يُحذف لاحقًا. نبحث في سجل التعديلات (diffs) ونستعرض نسخة الملف في الكوميت الذي يحتوي الباسورد.

### الأدوات

* `git log`
* `git show`
* `git log -p`
* `grep`

### خطوات تنفيذية 

```bash
# نفّذ هذا من جهازك المحلي
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
cd repo
```

2. تأكد من الفروع والـremotes:

```bash
git branch -a
```

3. استعرض سجلّ التغييرات على الملف المستهدف (مثلاً README.md):

```bash
git log -p -- README.md | grep 'password'
```

```
-- password: <no passwords in production!>
+- password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
 - password: <no passwords in production!>
+- password: <no passwords in production!>
```
4. استخدم بحث دقيق عن commit الذي أضاف/أزال سلسلة معينة:

```bash
git log -S'password' --all -p
# أو
git log -G'password|bandit30' --all -p
```

**تفسير:** `-S` يبحث عن تغيّر في عدد مرات ظهور السلسلة (أضيفت أو حُذفت). `-G` يبحث باستخدام تعابير نمطية (regex).

5. عند معرفة الـcommit hash (مثلاً `e50e6cc6...`) اعرض نسخة الملف كما كانت في ذلك الكوميت:

```bash
git show e50e6cc6be6bc718f834b1584971b1039e4e87db:README.md
```

**مثال مخرجات مهمة** (ما وجدت في الريبو):

```
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```

### سبب نجاح هذه الطريقة

لو صاحب الريبو أضاف الباسورد ثم غيّره لاحقًا، `git log -p` و `git show` يستعرضان هذه النقاط الزمنية بالضبط.

---


--- 

# تسجيل سريع للخطوات التي اتبعتها (

```bash
mkdir /tmp/bandit29 && cd /tmp/bandit29
# clone (من جهازك المحلي)
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
cd repo
# افحص الفروع
git branch -a
# راجع سجل README مع diff
git log -p -- README.md | grep 'password'
# بحث سريع
git log -S'password' --all -p
# لو تعرفت على commit hash، اعرض الملف كما كان
git show e50e6cc6be6bc718f834b1584971b1039e4e87db:README.md

```

---

## خاتمة

لقيت كلمة المرور داخل commit `e50e6cc6be6bc718f834b1584971b1039e4e87db` على الفرع `origin/dev`.

**Password for bandit30:** `qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL`

---
==لا تنسي الصلاه علي النب<mark style="background: #ADCCFFA6;"></mark>ي محمد ﷺ==

