
**الخطوات:**

1. **فحص الصفحة:**  
   - ستظهر الرسالة:
     ```
     Access disallowed. You are visiting from "" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"
     ```
   - هذا يعني أن الخادوم يتحقق من **Referer Header**

4. **حل المشكلة:**  
   - نحتاج لتغيير **Referer Header** في الطلب
   - يمكن فعل هذا باستخدام أدوات المطور في المتصفح أو باستخدام `curl`

5. **الطريقة الأولى: استخدام أدوات المطور (DevTools):**
   - افتح أدوات المطور (F12)
   - اذهب إلى Network tab
   - أنعش الصفحة (F5)
   - انقر على الطلب الأول (natas4)
   - انقر بزر الماوس الأيمن واختر "Copy as cURL"
   ```bash
   curl -H "Referer: http://natas5.natas.labs.overthewire.org/" \
        -u natas4:Z9tkRkWmpt9Qr7XrR5jWRkgOU901swEZ \
        http://natas4.natas.labs.overthewire.org/
   ```

5. **الطريقة الثالثة: باستخدام Burp Suite
غير من  
![[Screenshot From 2025-10-20 22-48-54.png]]
الي 
![[Screenshot From 2025-10-20 22-49-04.png]]
6. **النتيجة:**  
   - بعد إضافة الـ Referer الصحيح، ستحصل على كلمة المرور:
   ```
   Access granted. The password for natas5 is 0n35PkggAPm2zbEpOU802c0x0Msn1ToK
   ```

