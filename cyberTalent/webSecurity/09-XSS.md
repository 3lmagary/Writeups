## 1. What is XSS?

**Cross-Site Scripting (XSS)** هي ثغرة في تطبيقات الويب تعتمد على **حقن HTML أو تنفيذ JavaScript** داخل متصفح الضحية.

الهدف الأساسي للمهاجم غالبًا:

- سرقة **الكوكيز** أو **جلسة المستخدم**.
    
- تنفيذ أكواد خبيثة داخل المتصفح.
    

### مثال مبسط لكود ضعيف:

```php
<?php
echo "<h2>Welcome " . $_GET['username'] . "</h2>";
?>
```

إذا أدخل المستخدم البيانات:

```
http://example.com/index.php?username=hack
```

القيمة سيتم طباعتها في الصفحة مباشرة.

لكن إن أدخل:

```
http://example.com/index.php?username="><script>alert(1)</script>
```

سيتم تنفيذ الجافاسكربت — وهذه هي ثغرة XSS.

---

## 2. How to Test XSS?

### الخطوة 1 — تحديد **كل نقاط الإدخال**:

- GET parameters
    
- POST parameters
    
- Forms
    
- Cookies
    

### الخطوة 2 — تجربة **Payloads بسيطة**:

```
">
'>
<
>
/
&
```

### الخطوة 3 — تجربة **Payload XSS**:

```
"><script>alert(1)</script>
```

### الخطوة 4 — عند وجود فلترة، جرب **Encoding**:

- URL Encoding
    

```
%3Cscript%3Ealert(1)%3C/script%3E
```

- تغيير شكل السكربت:
    

```
<scr<script>ipt>alert(1)</scr<script>ipt>
```

### أنواع XSS:

#### 1) Reflected XSS

المدخلات تُعرض فورًا في الصفحة.

#### 2) Stored XSS

المدخل الخبيث يُخزَّن في قاعدة البيانات ويظهر لكل المستخدمين (مثال: التعليقات).

#### 3) DOM-Based XSS

التنفيذ يحدث داخل المتصفح بدون وصول الخبيث للسيرفر.

---

## 3. Impact — تأثير XSS

تستطيع XSS تمكين المهاجم من:

- سرقة الكوكيز
    
- سرقة الـ Session
    
- تنفيذ أكواد في المتصفح
    
- Keylogging
    
- Redirects خبيثة
    
- سرقة بيانات فور إدخالها (مثل فورم تسجيل الدخول)
    

---

## 4. Mitigation — كيفية الحماية

### يجب على المطورين:

1. **تصفية المدخلات Input Validation**
    
2. **ترميز المخرجات Output Encoding**  
    باستخدام:
    
    ```php
    htmlspecialchars()
    htmlentities()
    ```
    
3. **عدم الثقة بأي Input مهما كان**
    
4. **تفعيل Content Security Policy (CSP)**
    
5. **تجنب طباعة البيانات مباشرة بدون Sanitization**
    

مثال حماية:

```php
echo htmlspecialchars($_GET['username'], ENT_QUOTES, 'UTF-8');
```

---

## 5. Tools — أدوات مساعدة

- **Burp Suite**  
    لفحص نقاط الإدخال وتغيير/اعتراض الطلبات.
    
- **XSS-Proxy**  
    لاستغلال XSS والتحكم في الجلسة.
    
- **XSStrike**  
    أداة قوية لاكتشاف XSS مع bypass لبعض الفلاتر.
    
- **DalFox**  
    ماسح متخصص في XSS.
    

---

## مثال عملي لاختبار XSS في موقع:

### الإدخال:

```
username="><script>alert(document.cookie)</script>
```

### النتيجة:

ظهور alert يحتوي الكوكيز → الموقع ضعيف.

---
