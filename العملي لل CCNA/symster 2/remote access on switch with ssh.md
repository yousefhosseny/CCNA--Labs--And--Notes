
### **خطوات تفعيل Remote Access على السويتش باستخدام SSH**

#### 1. **تأكد من وجود IP على السويتش**

- لازم يكون عندك VLAN interface معمولها IP عشان تقدر توصله عن طريق الشبكة.  
    مثال:
    

```bash
S1# configure terminal
S1(config)# interface vlan 1
S1(config-if)# ip address 192.168.1.10 255.255.255.0
S1(config-if)# no shutdown
S1(config-if)# exit
```

- كده VLAN 1 خد عنوان IP.
    

---

#### 2. **تعيين Default Gateway (لو هتتصل من شبكة تانية)**

```bash
S1(config)# ip default-gateway 192.168.1.1
```

---

#### 3. **تفعيل الـ DNS Domain**

- لازم تضبط اسم دومين عشان توليد مفاتيح التشفير.
    

```bash
S1(config)# ip domain-name mynetwork.local
```

---

#### 4. **إنشاء User محلي (باسم وباسورد)**

- متقدرش تدخل SSH من غير يوزر:
    

```bash
S1(config)# username admin privilege 15 secret StrongPass123
```

🔹 `privilege 15` = يعني يوزر عنده صلاحيات كاملة.

---

#### 5. **توليد مفاتيح التشفير (RSA)**

- الأمر ده بيشغل الـ SSH.
    

```bash
S1(config)# crypto key generate rsa
How many bits in the modulus [512]: 1024
```

- اكتب 1024 أو 2048 عشان الأمان أعلى.
    

---

#### 6. **تفعيل الـ SSH على خطوط VTY**

- خطوط VTY هي اللي بتستخدم للاتصال عن بُعد (Telnet/SSH).
    

```bash
S1(config)# line vty 0 15
S1(config-line)# transport input ssh
S1(config-line)# login local
S1(config-line)# exit
```

🔹 `transport input ssh` = يمنع التلنت ويقبل SSH فقط.  
🔹 `login local` = يخلي الدخول باليوزر اللي أنشأته.

---

#### 7. **حفظ الإعدادات**

```bash
S1# copy running-config startup-config
```

---

#### 8. **التأكد من تفعيل SSH**

```bash
S1# show ip ssh
```

---

#### 9. **الاتصال من الكمبيوتر**

- افتح التيرمنال (أو CMD) واكتب:
    

```bash
ssh admin@192.168.1.10
```

🔹 هتدخل بيوزر `admin` وباسورد `StrongPass123`.

---

✅ **الخلاصة**:

1.  ء  IP للـ VLAN.
    
2. Default Gateway.
    
3. Domain Name.
    
4. User + Password.
    
5. Generate RSA Keys.
    
6. Configure VTY lines (SSH only).
    
7. Save config.
    
8. Connect via SSH client.
    

---
