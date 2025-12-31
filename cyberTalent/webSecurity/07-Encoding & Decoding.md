## What will you learn?

1. What are Encoding and Decoding?
    
2. Encoding Schemes Types
    
3. Practical Security Examples
    

---

# 1. What are Encoding and Decoding?

## Encoding

تحويل النصوص والرموز والبيانات إلى صيغة أخرى مناسبة **للنقل أو التخزين**.  
الهدف الأساسي: **التمثيل—not security**.

## Decoding

عكس عملية الـ Encoding لإعادة البيانات إلى شكلها الطبيعي.

## Notes

- HTTP وHTML بروتوكولات نصية، لذلك تحتاج طرقًا لتمثيل الأحرف الخاصة.
    
- **Encoding لا يوفّر حماية** ولا يجب استخدامه لحماية بيانات حساسة.
    

---

# 2. Encoding Schemes Types

## A. URL Encoding

يُستخدم لتمثيل الأحرف غير المسموح بها في الروابط.

- المسافة → `+` أو `%20`
    
- `%xx` تمثّل قيمة Hex
    

**Example:**

```
https://site.com/search?q=hello world
→ https://site.com/search?q=hello%20world
```

### Security Example

عند اختبار **URL Manipulation** أو **Parameter Pollution**، قد تحتاج لترميز payload مثل:

```
<script>alert(1)</script>
→ %3Cscript%3Ealert(1)%3C%2Fscript%3E
```

---

## B. HTML Encoding

يستخدم لحماية المتصفح من تنفيذ الأحرف الخطرة داخل صفحات HTML.

**Common Encodings:**

- `<` → `&lt;`
    
- `>` → `&gt;`
    
- `"` → `&quot;`
    

### Security Example

عند عرض قيمة مدخلة من المستخدم، الترميز يمنع XSS.

```
User Input: <script>alert(1)</script>
After HTML Encoding: &lt;script&gt;alert(1)&lt;/script&gt;
```

---

## C. Base64 Encoding

يمثّل البيانات الثنائية بشكل نصي قابل للإرسال.

- كل 3 بايت → 4 رموز Base64.
    

### Security Uses

- يستخدم في **Basic HTTP Authentication**:
    
    ```
    username:password  
    → base64 → dXNlcm5hbWU6cGFzc3dvcmQ=
    ```
    
- فحص **Obfuscated Payloads** في الهجمات (مثلاً JS أو PowerShell).
    

### Example

```
echo -n "admin:admin" | base64
→ YWRtaW46YWRtaW4=
```

---

## D. Hex & Unicode Encoding

تمثيل البيانات على شكل أرقام hex أو Unicode.

### Example

- `A` → `0x41`
    
- `<` → `\u003C`
    

### Security Example

قد يستخدم المهاجم Unicode Bypass لتجاوز الفلاتر:

```
<script>
→ \u003Cscript\u003E
```

---

# Practical Summary

|Scheme|Purpose|Security Relevance|
|---|---|---|
|URL Encoding|إرسال أحرف غير ASCII في الروابط|تحضير Payloads للهجمات (XSS, SQLi)|
|HTML Encoding|حماية المتصفح من تنفيذ الأحرف الخاصة|منع/اختبار XSS|
|Base64|تمثيل البيانات الثنائية بصيغة نص|يظهر في Auth, Tokens, Malware|
|Hex / Unicode|تمثيل رقمي للأحرف|Bypass و Obfuscation أثناء الهجمات|

---