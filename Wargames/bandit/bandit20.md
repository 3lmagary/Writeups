# حل Bandit Level 20 → 21

**التاريخ:** 2025-09-24

---

## الوصف

البرنامج `suconnect` (ملف setuid) يتصل على `localhost` على البورت الذي تُمرّره كـ argument، يقرأ سطرًا واحدًا من الاتصال ويقارنُه بكلمة سر المستوى السابق (bandit20). إذا كانت المطابقة صحيحة، سيُرسل لك عبر نفس الاتصال كلمة سر المستوى التالي (bandit21).


---

## المتطلبات

- الوصول إلى الجهاز المحلي حيث يوجد `suconnect` 
    
- أدوات: `nc` (netcat)
    
- تشغيل السيرفر **أولًا** ثم تشغيل `suconnect`.
    

---

## أمر جاهز (OpenBSD-style `nc`) — سطر واحد

**نافذة 1 (Server — شغّل أولًا):**
#nc 
```bash
echo "0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO" | nc -l localhost 3000 &
```
- **nc -l localhost 3000 هو سيرفر (listener )**
```
```bash
./suconnect 3000
```
- **./suconnect 3000 هو client يحاول الاتصال بالسيرفر على البورت 3000.**
---
## للتجربة علي جهازك ومعرفة الامر من جذوره 
**انشاء ملف Server.py  -----=======<  
#python
```python
# اعمل ملف Python لمحاكاة suconnect
import socket
import sys

def start_server(port):
    # الباسورد الصحيح
    correct_password = "my_password_123"
    
    # أنشئ سيرفر
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind(('localhost', port))
    server_socket.listen(1)
    
    print(f"Server listening on port {port}...")
    
    client_socket, address = server_socket.accept()
    print(f"Connection from {address}")
    
    # استقبل البيانات
    received_data = client_socket.recv(1024).decode().strip()
    print(f"Received: {received_data}")
    
    # تحقق من الباسورد
    if received_data == correct_password:
        response = "Next level password: abc123XYZ"
        print("Password correct! Sending response...")
    else:
        response = "Wrong password!"
        print("Wrong password received.")
    
    client_socket.send(response.encode())
    client_socket.close()
    server_socket.close()

if __name__ == "__main__":
    if len(sys.argv) != 2:
        print("Usage: python3 server.py <port>")
        sys.exit(1)
    
    port = int(sys.argv[1])
    start_server(port)
EOF
```

```bash
# اعطيه صلاحية التنفيذ
chmod +x server.py
```

```bash
# افتح ترمينال واحد للسيرفر
python3 server.py 3000

# افتح ترمينال ثاني للكلباينت
echo "my_password_123" | nc localhost 3000
```

---
### الخاتمة
==**لا تنسي الصلاه علي النبي محمد صلي الله عليه وسلم**==
==Don't forget to send blessings upon the Prophet Muhammad, peace be upon him.==