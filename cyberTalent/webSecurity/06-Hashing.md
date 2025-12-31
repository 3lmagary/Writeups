
## 1. Introduction

هذه الملاحظات تشرح فكرة **Hashing Functions** بشكل مختصر وواضح، مع تنظيم ماركداون، وإضافة أمثلة عملية وتطبيقات أمنية مستخدمة في الاختبارات والـCTFs.

---

## 2. What Are Hashing Functions?

**Hashing Functions** هي دوال **one-way** تحول أي بيانات إلى قيمة ثابتة الطول تسمى **hash**.

خصائصها:

- لا يمكن استرجاع النص الأصلي من الـhash.
    
- أي تغيير بسيط في البيانات ينتج قيمة مختلفة تمامًا.
    
- تستخدم في: التحقق من سلامة البيانات، تخزين كلمات المرور، التحقيقات الرقمية.
    

ولكن بعض الخوارزميات القديمة مثل **MD5** و **SHA-1** لم تعد آمنة بسبب وجود **Collisions**.

---

## 3. Types of Hashing Algorithms

### 3.1 MD5

- ينتج قيمة طولها **128-bit**.
    
- كان يُستخدم للتحقق من سلامة الملفات.
    
- به **collisions** فلا يستخدم للحماية القوية.
    

**مثال عملي:**

```bash
echo -n password | md5sum
# الناتج:
# 5f4dcc3b5aa765d61d8327deb882cf99
```

### 3.2 SHA-2

عائلة من الخوارزميات الأكثر أمانًا:

- SHA-224
    
- SHA-256 (الأكثر استخدامًا)
    
- SHA-384
    
- SHA-512
    

تستخدم بكثرة في **التحقيقات الرقمية**، **الـForensics**، و **تأمين الأنظمة**.

**مثال:**

```bash
echo -n password | sha256sum
```

---

## 4. String Hashing

هو تحويل **String** إلى قيمة Hash.

تطبيقاته:

- مقارنة البيانات.
    
- كشف التغيير على نصوص أو ملفات.
    
- CTF challenges مثل تحديد كلمة سر بعد معرفة hash.
    

**مثال عملي:**

```bash
echo -n admin123 | md5sum
```

---

## 5. File Hashing

يستخدم للتحقق من سلامة الملفات، ومراقبة التغيير، والتحقيقات.

### 5.1 Windows

```powershell
Get-FileHash C:\Users\User\Desktop\file.exe
```

By default → SHA-256

### 5.2 Linux

```bash
md5sum file.exe
sha256sum file.exe
```

---

## 6. Security Applications

### ✔ Integrity Verification

التحقق من أن الملف لم يتم التعديل عليه.

### ✔ Malware Analysis

عند فحص Malware يتم تبادل Hash كـIOC.

### ✔ Digital Forensics

تأكيد أن ملف الأدلة لم يتم تغييره.

### ✔ Password Cracking (CTFs)

عندما تجد Hash داخل challenge وتحتاج إلى كسره باستخدام tools:

- Hashcat
    
- John the Ripper
    

### ✔ Version Control & Storage Checks

كشف تلف الملفات أثناء النقل أو الحذف أو التخزين.

---

## 7. Conclusion

الـHashing من أهم الأدوات في الأمن السيبراني لأنه يسمح:

- بمعرفة أي تغيير على البيانات.
    
- بتتبع الملفات في التحقيقات.
    
- باستخدامه كـIOC في Threat Hunting.
    

وتذكر أن: **MD5 و SHA-1 غير آمنين** ويجب استخدام **SHA-256 أو أعلى** في أي نظام حديث.