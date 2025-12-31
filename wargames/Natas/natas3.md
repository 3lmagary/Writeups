
**الخطوات:**

1. **فحص الصفحة:**  
   - انقر بزر الماوس الأيمن واختر "View Page Source" أو استخدم `Ctrl+U`.
   - ستلاحظ التعليق:
     ```
     <!-- No more information leaks!! Not even Google will find it this time... -->
     ```

4. **تحليل التلميح:**  
   - يشير "Not even Google will find it" إلى `robots.txt`
   - ملف `robots.txt` يستخدم لمنع محركات البحث من فهرسة صفحات معينة.

5. **افحص `robots.txt`:**  
   - اذهب إلى: `http://natas3.natas.labs.overthewire.org/robots.txt`
   - ستجد:
     ```
     User-agent: *
     Disallow: /s3cr3t/
     ```

6. **استكشف الدليل `/s3cr3t`:**  
   - اذهب إلى: `http://natas3.natas.labs.overthewire.org/s3cr3t/`
   - سترى هناك ملفًا باسم `users.txt`.

7. **افتح `users.txt`:**  
   - اذهب إلى: `http://natas3.natas.labs.overthewire.org/s3cr3t/users.txt`
   - ستجد فيه:
     ```
     natas4:QryZXc2e0zahULdHrtHxzyYkj59kUxLQ
     ```

8. **كلمة مرور Natas4:**  
   - كلمة المرور لـ `natas4` هي: `QryZXc2e0zahULdHrtHxzyYkj59kUxLQ`
