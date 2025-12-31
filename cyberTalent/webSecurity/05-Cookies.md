## 1. What Are Cookies?

Cookies هي ملفات نصية صغيرة يخزنها المتصفح. الهدف الأساسي منها هو "تذكّر" المستخدم، مثل حفظ الـ **session** أو بيانات تسجيل الدخول.

**أمثلة على بيانات يتم حفظها:**

- username=user
    
- sessionid=ASD98sd09asd
    

عند زيارة أي صفحة، المتصفح يرسل الكوكيز إلى الخادم تلقائيًا.

---

## 2. Tools Needed

- **Cookie-Editor Extension**: إضافة للمتصفح تسمح بقراءة، تعديل، وحذف الكوكيز بسهولة.
    

---

## 3. Cookie Manipulation in JavaScript

يمكن للمتصفح تنفيذ 3 عمليات أساسية على الكوكيز:

- إنشاء Cookie
    
- قراءة Cookie
    
- تعديل Cookie
    
- حذف Cookie
    

---

## 4. Creating Cookies

### مثال 1: إنشاء Cookie بسيطة

```js
document.cookie = "username=admin";
```

### مثال 2: إضافة تاريخ انتهاء

```js
var expiry = "expires=Tue, 01 Jan 2030 12:00:00 UTC";
document.cookie = "username=admin; " + expiry;
```

### مثال 3: تحديد المسار

```js
document.cookie = "username=admin; path=/";
```

---

## 5. Reading Cookies

```js
console.log(document.cookie);
```

يعرض جميع الكوكيز الخاصة بالموقع.

---

## 6. Modifying Cookies

التعديل يتم بنفس طريقة الإنشاء:

```js
document.cookie = "username=newvalue";
```

---

## 7. Deleting Cookies

يتم الحذف بتعيين تاريخ قديم:

```js
document.cookie = "username=test; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;";
```

---

## 8. Function to Set a Cookie

```js
function setCookie(cname, cvalue, exdays) {
  const d = new Date();
  d.setTime(d.getTime() + (exdays*24*60*60*1000));
  let expires = "expires="+ d.toUTCString();
  document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/";
}
```

**شرح:**

- `cname`: اسم الكوكي
    
- `cvalue`: قيمتها
    
- `exdays`: عدد الأيام قبل انتهاء الكوكي
    

---

## 9. Security Applications & Real‑World Examples

### 9.1 Session Hijacking

إذا قدر مهاجم يحصل على Cookie فيها sessionid، يقدر ينتحل شخصية المستخدم.

### 9.2 Cookie Tampering

إذا التطبيق يعتمد على قيمة مخزنة في الكوكي بدون تحقق، يمكن للمهاجم تعديلها.  
مثال:

```js
role=user  →  attacker edits → role=admin
```

### 9.3 CSRF & Cookies

الكوكيز تُرسل تلقائيًا، وهذا هو السبب في إمكانية استغلال CSRF.

### 9.4 XSS + Cookies

XSS يمكن يستخدم لسرقة الكوكي عبر:

```js
<script>alert(document.cookie)</script>
```

### 9.5 Secure Flags

لحماية الكوكيز:

- `HttpOnly`: يمنع JavaScript من قراءتها
    
- `Secure`: ترسل فقط عبر HTTPS
    
- `SameSite`: تحمي من CSRF
    

---

## 10. Summary

- الكوكيز جزء أساسي في إدارة الجلسات.
    
- يمكن التلاعب بها باستخدام JavaScript.
    
- تأمين الكوكيز ضروري لمنع سرقة الجلسات والتلاعب بالأدوار.
    
- معرفة التعامل معها مهم جدًا في أي اختبار اختراق Web.
    

---