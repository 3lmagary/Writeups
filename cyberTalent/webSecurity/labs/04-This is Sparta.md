# [Penetration Testing Report – "This is Sparta" Challenge (Web Security)](https://cybertalents.com/learn/introduction-to-cybersecurity/units/t-introduction-to-cybersecurity/lessons/4-javascript/challenges/this-is-sparta)

**Category:** Web Security  
**Level:** Easy  
**Points:** 50

---

## 1. Introduction

This report documents the analysis and exploitation steps performed on the CyberTalents challenge **“This is Sparta”**. The objective is to identify weaknesses in client-side JavaScript logic and retrieve the valid flag.

---

## 2. Overview

Challenge URL:  
`http://cdlemkm73pw7hqzqw4m2360mtg301w93xnjq4i7vr-web.cybertalentslabs.com`

The page displays a simple login form with **Username** and **Password** fields plus a **Hint** button.

---

## 3. Technical Analysis

Inspecting the HTML shows a JavaScript function named `check()` that performs client-side validation:

```js
var _0xae5b=[
  "\x76\x61\x6C\x75\x65",     // "value"
  "\x75\x73\x65\x72",         // "user"
  "\x67\x65\x74\x45\x6C\x65\x6D\x65\x6E\x74\x42\x79\x49\x64", // "getElementById"
  "\x70\x61\x73\x73",         // "pass"
  "\x43\x79\x62\x65\x72\x2d\x54\x61\x6c\x65\x6e\x74",  // <-- Important string
  "\x20...Congratulations...",
  "\x77\x72\x6F\x6E\x67\x20\x50\x61\x73\x73\x77\x6F\x72\x64"
];
```


encode
```javascript
function check() {

    var user_value = document.getElementById("user").value;
    var pass_value = document.getElementById("pass").value;

    if (user_value == "Cyber-Talent" && pass_value == "Cyber-Talent") {
        alert("                    Congratz \n\n");
    } else {
        alert("wrong Password");
    }
}
```

The username and password are compared against the value at index **4** of the array.

---

## 4. Decoding Obfuscated JavaScript

The important string is:

```
"\x43\x79\x62\x65\x72\x2d\x54\x61\x6c\x65\x6e\x74"
```

Converting this hex-encoded string to text gives:

```
Cyber-Talent
```

This means: **Username = Cyber-Talent** and **Password = Cyber-Talent**.

decode 
```python
python3 -c "print(b'\x43\x79\x62\x65\x72\x2d\x54\x61\x6c\x65\x6e\x74'.decode('utf-8'))"
```

```bash
echo "\x43\x79\x62\x65\x72\x2d\x54\x61\x6c\x65\x6e\x74"
```

```js
console.log("\x43\x79\x62\x65\x72\x2d\x54\x61\x6c\x65\x6e\x74")
```

---

## 5. Exploitation

Enter:

- **Username:** Cyber-Talent
    
- **Password:** Cyber-Talent
    

This triggers the JavaScript success alert containing: “Congratulations”.

---

## 6. Flag Retrieval

The challenge description specifies the format: `{flagbody}`.

Since the correct credential is the core logic of the challenge, the flag body is:

```
{J4V4_Scr1Pt_1S_Aw3s0me}
```

---

## 7. Conclusion

- JavaScript obfuscation often uses hex-encoded strings.
    
- Always inspect client-side scripts in easy-level challenges.
    
- Array index values frequently hide credentials or flags.
    

---