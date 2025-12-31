# [Introduction to Cyber security](https://cybertalents.com/learn/introduction-to-cybersecurity/units/t-introduction-to-cybersecurity/lessons/1-introduction-to-ctf)

## ما هو الـ CTF؟

**CTF = Capture The Flag**  
هو نوع من مسابقات الأمن السيبراني. بتكون قدّامك **Challenge** فيها ثغرة أو مشكلة أمنية، وتستخدم مهاراتك علشان **تستغل الثغرة** وتلاقي حاجة اسمها **Flag**.

**الـ Flag** هو نص (String) بيثبت إنك حلّيت التحدي.  
أمثلة:

```
flag{Th1s_1s_c00l_fl1g}
flag{9e58967420ac5b2d87578e88b389e306}
```

الـ CTF ممكن تلعبه:

- فردي
    
- كفريق (على حسب قوانين المسابقة)
    

وهي بتحاكي سيناريوهات حقيقية للثغرات.

---

# أنواع مسابقات CTF

## 1) Jeopardy-Style CTF

هو أشهر نوع. بيكون فيه تصنيفات (Categories) وكل تحدي عليه **Points** حسب الصعوبة.

أهم التصنيفات:

### 1. Cryptography

فهم خوارزميات التشفير زي:

- RSA
    
- AES
    
- DES  
    وأحيانًا تشفير Custom لازم تفهمه علشان تعمل **Decrypt** للرسالة.
    

### 2. Digital Forensics

تحليل:

- الـ File formats
    
- Steganography (إخفاء البيانات داخل صور/ملفات)
    
- Memory dumps
    
- PCAP (تحليل ترافيك الشبكات)
    

### 3. Reverse Engineering

تحليل ملف تنفيذي زي:

- exe
    
- apk  
    وتحويله لـ كود أقرب للي البشر يفهموه علشان تفهم سلوكه.
    

### 4. Web Security

اكتشاف واستغلال ثغرات الويب:

- SQL Injection
    
- XSS
    
- LFI/RFI
    
- Authentication bypass  
    ... إلخ
    

### 5. Exploitation (Pwn)

استغلال خدمات أو ملفات binaries للوصول للـ Flag.  
هنا بيستخدموا تقنيات Reverse + Buffer Overflow + ROP… إلخ.

### 6. Network Security

تحليل ترافيك الشبكة (pcap وغيره).

### 7. OSINT

استخدام أدوات ومصادر مفتوحة لجمع معلومات عن Target.

### 8. Machines

زي TryHackMe و HackTheBox.  
تعمل:

- Scan
    
- Exploit
    
- Escalate Privileges  
    لحد ما تقرأ الـ Flag.
    

---

## 2) Attack-Defense CTF

كل فريق عنده شبكة أو جهاز فيه ثغرات.  
المطلوب:

- **تأمّن جهازك** علشان تكسب Defense points
    
- **تهاجم أجهزة الفرق التانية** علشان تكسب Attack points
    

هذا النوع أصعب واحترافي أكثر.

---

# المهارات المطلوبة للّعب في CTF

## مهارات مشتركة مهمة:

- أساسيات Network
    
- لغات برمجة (خصوصًا Python)
    
- Linux Command Line
    
- C / C++ و Assembly لو داخل Reverse
    

## المهارات حسب كل تخصص:

### 1) Web Exploitation

- أساسيات لغات الويب
    
- OWASP Top 10
    

### 2) Machines

- أساسيات Penetration Testing
    
- معرفة Web Exploitation
    

### 3) Cryptography

- أساسيات رياضيات
    
- أنواع التشفير Symmetric & Asymmetric
    

### 4) Reverse Engineering

- فهم Assembly
    
- Debugging
    
- أدوات مثل Ghidra / IDA / Radare / x64dbg
    

**أهم مهارة:**  
الاستمرارية. مفيش حد بيحل Challenges من أول يوم. لازم تجربة وفشل ومحاولات.

---

# لماذا الـ CTF مهم في تعلم Cybersecurity؟

- بيقوّي مهاراتك التقنية بشكل كبير.
    
- بعض الشركات الكبيرة بتركّز قوي على اللاعبين اللي رتبهم عالية في CTF competitions.
    
- بيعرّفك نقاط ضعفك.
    
- بيطوّر طريقة تفكيرك أثناء الاختراق الحقيقي.
    
- بيرفع مستواك ويزيد Networking مع المجتمع التقني.
    
- بيخلّيك تتعلم بسرعة لأنك بتحل مشاكل حقيقية.
    
- بعض المسابقات عندها جوائز قوية.
    
- ممكن شركات تكلمك مباشرة لو ترتيبك عالي.
    
---

# كيف تتعلم أكثر عن الـ CTF؟

أفضل طريقة: **Practice**

منصات للممارسة:

- CyberTalents
    
- PicoCTF
    
- PortSwigger (Web)
    
- RootMe (Web + Reverse + Other)
    
- CryptoHack
    
- CyberDefenders
    
- TryHackMe
    
- HackTheBox
    

ابدأ من Challenges سهلة.  
لو وقفت: اقرأ **Writeups** واعرف الغلطة اللي عملتها.

---

# كيف تشارك في مسابقات CTF؟

المنصة الأساسية:

- **ctftime.org**
    

هتلاقي:

- كل المسابقات القادمة
    
- لينكات التسجيل
    
- Writeups للمسابقات القديمة
    

وبرضه مسابقات CyberTalents نفسها تبقى معلنة على موقعهم.

<mark style="background: #FF5582A6;">16 - 11 - 2025</mark>
