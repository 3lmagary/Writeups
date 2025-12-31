# حل مستوى Bandit 12
**التاريخ:** 2025-09-18  
**المصدر:** OverTheWire — Bandit

---

## 🎯 الهدف (Goal)
> Find the password for the next level (bandit13).  
> The password is stored in the file `data.txt`, which is a hexdump of a file that has been repeatedly compressed.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `xxd` - لتحويل hexdump إلى ملف ثنائي
- `file` - للتحقق من نوع الملف
- أدوات فك الضغط المختلفة
- `gzip -d` - لفك ضغط ملف `.gz`
- `bzip2 -d` - لفك ضغط ملف `.bz2`
- `tar -xf` - لفك ضغط ملف `.tar`

---

## 🚀 طريقة الحل (Solution Steps)

1. **الاتصال بالخادم**

```bash
ssh -p 2220 bandit12@bandit.labs.overthewire.org
# أدخل كلمة مرور المستوى 11: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

2. **إنشاء مجلد عمل مؤقت ونسخ الملف**

```bash
cd $(mktemp -d)
cp ~/data.txt .
```

3. **تحويل الملف من hexdump إلى ملف ثنائي**

```bash
xxd -r data.txt > data.bin
rm data.txt
```

4. **فك طبقات الضغط المتعددة**

استمر في فك الضغط حتى الوصول للملف النهائي. الأمثلة أدناه توضح الخطوات المتتابعة التي قمت بها (المسميات قد تختلف حسب ما ينتج من الملفات أثناء كل خطوة):

```bash
# الطبقة الأولى: gzip
mv data.bin data.gz
gzip -d data.gz

# الطبقة الثانية: bzip2
mv data data.bz2
bzip2 -d data.bz2

# الطبقة الثالثة: gzip
mv data data.gz
gzip -d data.gz

# الطبقة الرابعة: tar
mv data data.tar
tar -xf data.tar
rm data.tar

# الطبقة الخامسة: tar (مثال لمسميات مختلفة)
mv data5.bin data.tar
tar -xf data.tar
rm data.tar

# الطبقة السادسة: bzip2
mv data6.bin data.bz2
bzip2 -d data.bz2

# الطبقة السابعة: tar
mv data data.tar
tar -xf data.tar
rm data.tar

# الطبقة الثامنة: gzip
mv data8.bin data.gz
gzip -d data.gz
```

5. **قراءة كلمة المرور**

```bash
cat data
```

---

## 🔑 النتيجة (Result)
**كلمة مرور المستوى 13:** `FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

---

## 💡 ملاحظات (Notes)
- تم استخدام مجلد مؤقت (`/tmp` أو ما يعادله عبر `mktemp`) للعمل فيه لتجنب مشاكل الصلاحيات.
- استخدمنا `file` بشكل متكرر لتحديد نوع الملف وتحديد الأداة المناسبة لفك الضغط.
- كل طبقة ضغط تحتاج إلى التعامل معها بالأداة المناسبة (gzip, bzip2, tar, ...).
- العملية تتطلب الصبر والتكرار حتى الوصول للملف النهائي.
- المرحلة التالية: Bandit Level 13 → Level 14

---

## 🚀 طريقة الحل التلقائية (Automated Solution)

```bash
# إنشاء مجلد مؤقت والانتقال إليه
cd $(mktemp -d)

# نسخ ملف البيانات
cp ~/data.txt .

# تحويل hexdump إلى ملف ثنائي
xxd -r data.txt > data
rm data.txt

# حلقة تلقائية لفك جميع طبقات الضغط
while true; do
    file_desc=$(file data)

    if echo "$file_desc" | grep -q "gzip"; then
        mv data data.gz
        gzip -d data.gz
    elif echo "$file_desc" | grep -q "bzip2"; then
        mv data data.bz2
        bzip2 -d data.bz2
    elif echo "$file_desc" | grep -q "tar" || echo "$file_desc" | grep -q "POSIX"; then
        mv data data.tar
        tar -xf data.tar
        rm -f data.tar
        # إذا كان الأرشيف يحتوي على ملف وحيد اسمه مختلف
        # حاول إعادة تسميته إلى 'data' لتكرار العملية
        ls -1 | grep -E '^data|^data[0-9]*' || true
        # محاولة جمع الملفات الناتجة في ملف 'data' (إذا لزم الأمر)
        # mv "$(ls -1 | head -n1)" data 2>/dev/null || true
    elif echo "$file_desc" | grep -q "ASCII" || echo "$file_desc" | grep -q "text"; then
        # وجدنا الملف النهائي (نص عادي)
        break
    else
        echo "نوع ملف غير معروف: $file_desc"
        exit 1
    fi
done

# عرض كلمة المرور
cat data
```

---

**انتهى**

