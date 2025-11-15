
## Connection Details

- **SSH Command:** `ssh leviathan0@leviathan.labs.overthewire.org -p 2223`
    
- **Password:** `leviathan0`
    
- data: 15-11-2025
---

## Step 1: Initial Enumeration

بعد تسجيل الدخول:

```bash
ls
```

لم يظهر شيء، لذلك تم استخدام:

```bash
ls -lah
```

النتيجة:

- مجلد مخفي باسم `.backup`
    
- المجلد مملوك للمستخدم `leviathan1` لكن قابل للقراءة بواسطة `leviathan0`
    

---

## Step 2: استكشاف مجلد `.backup`

```bash
cd .backup
ls
```

ظهر ملف:

- `bookmarks.html`
    

---

## Step 3: قراءة ملف `bookmarks.html`

الملف يحتوي على عدد كبير من الروابط. للعثور على أي شيء مهم:

```bash
cat bookmarks.html | grep 'password'
```

النتيجة:

```
<DT><A HREF="http://leviathan.labs.overthewire.org/passwordus.html | This will be fixed later, the password for leviathan1 is 3QJ3TgzHDq" ...>password to leviathan1</A>
```

### النتيجة:

- **Password for leviathan1:** `3QJ3TgzHDq`
    

---

## Step 4: الدخول إلى المستخدم التالي

```bash
ssh leviathan1@leviathan.labs.overthewire.org -p 2223
```

كلمة المرور:

```
3QJ3TgzHDq
```

---

## Alternate Approach

بدل `grep`، يمكن استخدام `strings` لتصفية النصوص:

```bash
strings bookmarks.html | grep -i pass
```

أو استخدام `less` والبحث داخله:

```bash
less bookmarks.html
```

الضغط على `/` ثم كتابة:

```
password
```

---

## Summary

- المجلد `.backup` يحتوي على ملف HTML به بيانات حساسة.
    
- استخراج كلمة مرور `leviathan1` تم بسهولة عبر `grep`.
    