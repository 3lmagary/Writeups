
**الخطوات:**

1. **فحص الصفحة:**  
   - انقر بزر الماوس الأيمن واختر "View Page Source" أو استخدم `Ctrl+U`.
   - لاحظ وجود صورة باسم `pixel.png`.

4. **افحص ملف `pixel.png`:**  
   - انقر بزر الماوس الأيمن على الصورة واختر "Inspect" أو "Inspect Element".
   - لاحظ أن الصورة يتم تحميلها من: `/files/pixel.png`

5. **استكشف دليل `/files`:**  
   - اذهب إلى: `http://natas2.natas.labs.overthewire.org/files/`
   - سترى هناك ملفًا باسم `users.txt`.

6. **افتح `users.txt`:**  
   - اذهب إلى: `http://natas2.natas.labs.overthewire.org/files/users.txt`
   - ستجد فيه:
     ```
     # username: password
     alice:BYNdCesZqW
     bob:jw2ueICLvT
     charlie:G5vCxkVV3m
     natas3:3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH
     eve:zo4mJWyNj2
     mallory:9urtcpzBmH
     ```

