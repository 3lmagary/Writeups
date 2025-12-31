
# الدرس: Introduction to JavaScript for Cybersecurity

## ما الذي ستتعلمه؟

1. What is JavaScript?
    
2. JavaScript Examples
    
3. How to Run JS?
    
4. Using JS in Testing for XSS
    

---

# 1) ما هو JavaScript؟

**JavaScript** لغة برمجة تُستخدم في:

- **Front-End**
    
- **Back-End**
    
- **Full-Stack Development**
    

وهي **client-side scripting language** بتخلي صفحات الويب **Dynamic** و **Interactive**.

## علاقتها بالأمن السيبراني

في **Penetration Testing** لازم تكون فاهم JavaScript كويس علشان:

- تحلل كود الويب
    
- تكتشف ثغرات **Client-Side**  
    زي:
    
- XSS
    
- CSRF
    
- DOM Manipulation vulnerabilities
    

## أين نكتب JavaScript؟

يوضع داخل صفحة HTML:

```html
<script>
    // JS code
</script>
```

أو في ملف خارجي:

```html
<script src="main.js"></script>
```

---

# 2) JavaScript Examples

### document.write()

يكتب بيانات مباشرة داخل صفحة HTML.

### window.location.hostname

يجلب **Hostname** الخاص بالموقع  
مثل:

```
www.example.com
```

### console.log()

يطبع نص داخل Console المتصفح.  
مفيد جدًا أثناء الاختبار.

### alert()

يظهر نافذة Pop-up بالرسالة التي تضعها.  
وهو أكثر Function تستخدم في اختبار XSS.

---

# 3) كيف تشغّل JavaScript؟

متصفحات مثل **Firefox** و **Chrome** فيها JavaScript Engine مدمج.

### تشغيل JavaScript من الـ Console:

1. اضغط Right-Click في الصفحة
    
2. اختر **Inspect**
    
3. افتح تبويب **Console**
    
4. اكتب أي كود مثل:
    

```js
alert('JavaScript Test')
```

سيظهر Pop-up برسالتك.

---

# 4) استخدام JavaScript في اختبار XSS

**XSS = Cross-Site Scripting**  
ثغرة تعتمد على حقن JavaScript في الموقع.

الأنواع:

- Reflected XSS
    
- Stored XSS
    
- DOM-Based XSS
    

### متى تظهر Vulnerability؟

لو التطبيق:

- لا يعمل Sanitization
    
- لا يعمل Encoding
    
- يطبع المدخلات مباشرة في الصفحة
    

---

# DOM-Based XSS

وهي أصعب نوع لأنها لا تحتاج سيرفر.  
المشكلة في الكود داخل الصفحة نفسها.

## مثال :

الصفحة تستخدم:

```js
document.location.href
document.write()
```

- `document.location.href` مصدر (Source)
    
- `document.write()` مخرج (Sink) يطبع مباشرة في الـ DOM
    

**بدون Sanitization** تقدر تحقن كود JS في الـ URL:

```
#<script>alert('xss')</script>
```

لما الصفحة تنفّذ:

- `document.write()` يكتب الكود في HTML
    
- الكود يشتغل
    
- يظهر alert
    

---

# ما هي Sources و Sinks؟

## Sources

أماكن **تحصل منها الصفحة على بيانات** المستخدم.  
أمثلة:

- `document.URL`
    
- `document.location`
    
- `document.referrer`
    

## Sinks

أماكن **يتم تنفيذ البيانات فيها كـ JavaScript**  
أمثلة:

- `eval()`
    
- `document.write()`
    
- `innerHTML`
    
- `setTimeout()` مع String
    

لو الـ Source يروح للـ Sink بدون فلاتر → DOM XSS.

---

# JavaScript لا يستخدم فقط لـ XSS

أيضًا مهم في ثغرات ثانية مثل:

### CSRF

أحيانًا يتم استخدامها بحقن JS يجبر المستخدم يعمل Action غصب عنه.

---

# الهدف الأساسي من حقن JavaScript

المهاجم يريد:

- سرقة **session cookies**
    
- تشغيل أوامر في الصفحة
    
- تحويل المستخدم لروابط خبيثة
    
- تنفيذ أفعال بدون علمه (CSRF + XSS)
    

---
