# [Searching for the Cookie – Web Challenge](https://cybertalents.com/learn/introduction-to-cybersecurity/units/t-introduction-to-cybersecurity/lessons/9-xss/challenges/searching-for-the-cookie)

---

## 1. فكرة التحدي

الموقع يحتوي على صفحة **بحث بسيطة**. أي نص تكتبه في خانة البحث يتم عرضه مرة أخرى داخل **سكريبت JavaScript** في السورس كود.  
لكن الموقع لا يقوم بتعقيم (sanitize) المدخلات، مما يسمح بـ **DOM XSS**.

الهدف: تشغيل **JavaScript** داخل الصفحة للحصول على **الكوكي** الذي يحتوي على الفلاج.

---

## 2. خطوات استكشاف الثغرة

### الخطوة 1: تجربة إدخال سكريبت

عند كتابة:

```html
<script>alert(2)</script>
```

لن يظهر أي alert في الصفحة، لكن عند فتح السورس (Ctrl + U) ستجد:

```html
<script>var currentSearch = {'keyword':'you searched for: <script>alert(2)</script>'};</script>
```

هذا يعني أن الإدخال يُحقن **داخل سكريبت** موجود بالفعل، لذلك تنفيذ الكود لم يتم.

---

## 3. كيفية استغلال الحقن

لكي يتم تنفيذ كود JavaScript من إدخالنا، نحتاج إلى:

1. **إغلاق** السكريبت الأصلي.
    
2. **فتح سكريبت جديد** خاص بنا.
    
3. **كتابة أمر alert**.
    

لذلك نستخدم:

```html
</script><script>alert(2)</script>
```

وهنا يتم إغلاق التاج الأول، ثم فتح تاج جديد يتم تنفيذه فعلاً.

---

## 4. استخراج الكوكي (الفلاج)

بعد التأكد من أن XSS تعمل، نستخدم:

```html
</script><script>alert(document.cookie)</script>
```

سيظهر alert فيه الكوكي الخاصة بالمستخدم.  
الكوكي تحتوي على الفلاج، وكانت:

```
coolcookie112
```

---

## 5. الفلاج

**coolcookie112**

---