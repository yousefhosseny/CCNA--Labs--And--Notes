تمام ✅ هنضيف كمان جزء خاص بخطوات **إرجاع الترنك للإعدادات الافتراضية** في الـ Cheat Sheet بتاعك، بحيث يبقى كامل ومرتب.

---


### 1️⃣ تحويل المنفذ إلى Trunk

```bash
Switch# configure terminal
Switch(config)# interface fa0/1
Switch(config-if)# switchport mode trunk
```

### 2️⃣ إعدادات اختيارية 

- تغيير الـ Native VLAN:
    

```bash
Switch(config-if)# switchport trunk native vlan 99
```

- تحديد الـ VLANs المسموح بها:
    

```bash
Switch(config-if)# switchport trunk allowed vlan 10,20,30,99
```

- إلغاء التفاوض التلقائي (DTP):
    

```bash
Switch(config-if)# switchport nonegotiate
```

### 3️⃣ إرجاع الترنك للإعدادات الافتراضية

- رجع البورت لوضع **Access** (إلغاء الـ trunk):
    

```bash
Switch(config-if)# switchport mode access
```

- رجع الـ Native VLAN للوضع الافتراضي (VLAN 1):
    

```bash
Switch(config-if)# no switchport trunk native vlan
```

- رجع قائمة الـ VLANs المسموح بها للوضع الافتراضي (كل VLANs):
    

```bash
Switch(config-if)# no switchport trunk allowed vlan
```

- رجع التفاوض (DTP) للوضع الافتراضي:
    

```bash
Switch(config-if)# no switchport nonegotiate
```

### 4️⃣ التحقق

- عرض الترونكات النشطة:
    

```bash
show interfaces trunk
```

- عرض حالة البورت:
    

```bash
show interface fa0/1 switchport
```

- عرض VLANs:
    

```bash
show vlan brief
```

---

تحب أجهزلك نسخة **PDF صغيرة كـ Cheat Sheet مرتب** للأوامر دي كلها علشان تذاكر وتطبعها؟


### الشرح العملي

![[2025-09-27 11-31-25.mkv]]