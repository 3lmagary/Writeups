# حل مستوى Bandit 14 → Bandit 15

**التاريخ:** 2025-9-20\
**المصدر:** OverTheWire — Bandit

---

## 🎯 الهدف (Goal)

> The password for the next level can be retrieved by submitting the password of the current level to port 30000 on `localhost`.

## 🔧 الأدوات المستخدمة (Tools Used)

- `nc` (netcat) - للاتصال بـ TCP socket على البورت 30000.
- `echo` / `cat` - لإرسال كلمة المرور الحالية عبر الاتصال.

## 🚀 طريقة الحل (Solution Steps)

### Bandit13

- MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

### 2. إرسال كلمة المرور إلى الخادم على البورت 30000
#nc
```bash
echo "MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS" | nc localhost 30000
```

### --- 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
