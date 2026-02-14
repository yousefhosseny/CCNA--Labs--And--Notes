
## 🎯 السيناريو:

- عندنا شبكة: **192.168.1.0/24**
    
- الراوتر عنوانه (Gateway): **192.168.1.1**
    
- عايزين نوزع عناوين للأجهزة من **192.168.1.11 → 192.168.1.254**
    
- DNS Server: **8.8.8.8**
    
- مدة الـ Lease: **1 يوم**
    

---

## 🖥️ خطوات الإعداد على الراوتر:

```bash
# ندخل وضع الضبط
Router> enable
Router# configure terminal

# 1) استثناء العناوين (Gateway أو عناوين ثابتة)
Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10

# 2) إنشاء Pool جديد اسمه MYPOOL
Router(config)# ip dhcp pool MYPOOL
Router(dhcp-config)# network 192.168.1.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.1.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# domain-name mynetwork.local
Router(dhcp-config)# lease 1

# نرجع للوضع العادي
Router(dhcp-config)# exit
Router(config)# exit
Router#
```

---

## 📊 التحقق من الإعدادات:

1. نشوف الـ DHCP Config:
    

```bash
Router# show running-config | section dhcp
```

2. نشوف الـ Bindings (الأجهزة اللي خدت IP):
    

```bash
Router# show ip dhcp binding
```

3. نشوف إحصائيات السيرفر:
    

```bash
Router# show ip dhcp server statistics
```

---

## 🖥️ على جهاز Client (مثلاً PC في Packet Tracer):

```bash
C:\> ipconfig /all
```

- هتلاقي إن الجهاز خد IP أوتوماتيك من الراوتر (مثلاً 192.168.1.11).
    
- الـ Default Gateway: 192.168.1.1
    
- الـ DNS: 8.8.8.8
    

---

## 💡 ملحوظة:

لو عندك شبكة تانية والأجهزة هناك محتاجة IP من نفس السيرفر ده → لازم تضبط الراوتر بتاع الشبكة التانية كـ **Relay Agent**:

```bash
Router(config-if)# ip helper-address 192.168.1.1
```

---

