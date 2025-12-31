# What will you learn?

1. Tools Needed
2. What is HTML?
3. Example for Creating a Webpage
4. Why do you need to Learn HTML Basics?

---

## Tools Needed

* Web Developer Tools

---

## What is HTML?

**HTML** هي *HyperText Markup Language*.
ليست لغة برمجة، بل تُستخدم لإنشاء صفحات الويب أو المستندات التي يعرضها المتصفح.

تُستخدم مع:

* **CSS** لتحسين شكل الصفحة
* **JavaScript** لإضافة التفاعل

مفاهيم أساسية:

* HTML تحتوي على **عناصر (Elements)**
* كل عنصر يُعرّف بواسطة **وسم (Tag)**
* الوسوم قد تحتوي على **خصائص (Attributes)**

تاريخ HTML:

* أول إصدار: **HTML 1.0**
* أحدث إصدار: **HTML5** مع ميزات جديدة

---

## Example for Creating a Webpage

```html
<!DOCTYPE html>
<html>
<head>
    <title>My First Page</title>
</head>
<body>
    <h1>Hello World</h1>
</body>
</html>
```

### شرح العناصر:

* `<!DOCTYPE html>`
  يخبر المتصفح أن الملف يستخدم HTML.

* `<html>`
  يحتوي جميع عناصر الصفحة.

* `<head>`
  يضم عناصر مثل `<title>` و `<link>` وغيرها.

* `<title>`
  يظهر نصه في تبويب المتصفح.

* `<body>`
  يحتوي عناصر الصفحة المرئية مثل الصور والروابط.

* `<h1>`
  عنصر عناوين رئيسية (من h1 إلى h6).

### عرض المصدر

لمشاهدة الكود:

* Right-click → Inspect
* أو View Page Source

يمكن رؤية العناصر المخفية أيضًا.
يستطيع المطور إخفاء العناصر باستخدام:

* CSS
* السمة `hidden`

---

## Why do you need to Learn HTML Basics?

أساسيات HTML ضرورية في **اختبار اختراق الويب** لأنها تفيد في فهم:

* طريقة إدخال البيانات
* طريقة عرض العناصر
* كيفية استغلال بعض الثغرات مثل **XSS**

### مثال HTML يُستخدم في اختبار XSS:

```html
<video>
    <source src="x" onerror="alert(1)">
</video>
```

عند فشل تحميل المصدر، يتم تشغيل **onerror** وتشغيل `alert(1)`.

---
