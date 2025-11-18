# حل مستوى Bandit 31 → 32

**التاريخ:** 2025-10-19
**المصدر:** OverTheWire — Bandit

---

## 🎯 الهدف (Goal)

ادفع ملفًا باسم `key.txt` إلى الريبو البعيد على الفرع `master` بحيث يقبل الخادم الملف أو يُظهِر للمستخدم كلمة مرور المستوى التالي.

**التفاصيل المطلوبة:**

* اسم الملف: `key.txt`
* المحتوى: `May I come in?` 
* الفرع: `master`

---

## ✅ ما قمت به عمليًا 

1. ```bash
   mkdir tmp/bandit31 && cd tmp/bandit31
   ```

2. ```bash
   git clone ssh://bandit31-git@bandit.labs.overthewire.org:2220/home/bandit31-git/repo
   
   cd repo
   ```
2. معرفه محتوي `README.md`
```bash
cat README.md
```

```text
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```
3. انشاء ملف `key.txt` و بداخله المحتوي المطلوب 
```bash
echo "May I come in?" > key.txt
```

2. عند  محاولة `git add key.txt` ظهر تحذير لأن `.gitignore` يحتوي نمطًا يمنع إضافة `*.txt`:

```text
The following paths are ignored by one of your .gitignore files:
key.txt
hint: Use -f if you really want to add them.
```

3. استخدمت القوة لإجبار Git على إضافة الملف (force add):

```bash
git add -f key.txt
git commit -m "Add key.txt for bandit31 challenge"
```

4. ثم دفعّت (push) التغيير إلى الريبو البعيد:

```bash
git push origin master
```

---

## 🔍 ما طبعه الخادم (Server output) وشرح كل جزء

عند تنفيذ `git push origin master` وصلتك هذه المخرجات من الخادم:

```
remote: ### Attempting to validate files... ####
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
remote: Well done! Here is the password for the next level:
```

remote: <mark style="background: #ADCCFFA6;">3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K</mark>

```
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
```

---

## ✅ النتيجة النهائية

**كلمة مرور bandit32 هي:**

```
3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
```

---

## نقاط مهمة  

* وجود `.gitignore` الذي يمنع `*.txt` كان خطوة مقصودة: التحدي يريدك تُجبَر على استخدام `git add -f` لمعرفة التعامل مع ملفات متجاهلة.

---

##  مرجع سريع

```bash
# إنشاء الملف
echo "May I come in?" > key.txt

# إجبار git لإضافة الملف حتى وإن كان متجاهلاً
git add -f key.txt

# عمل commit
git commit -m "Add key.txt for bandit31 challenge"

# دفع التغيير
git push origin master
```

---

<mark style="background: #BBFABBA6;">لا تنسي الصلاه علي النبي محمد </mark>

