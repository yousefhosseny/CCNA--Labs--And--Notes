تمام 👌 هكتبلك الـ **Cheat Sheet بتاع DTP** كله هنا نصيًا زي ما في الـ PDF:

---

# 📘 Dynamic Trunking Protocol (DTP) – Cheat Sheet

## 1️⃣ الوضع الافتراضي

- DTP مفعّل تلقائيًا على سويتشات Cisco Catalyst (زي 2960, 2950).
    
- الوضع الافتراضي:
    

```
switchport mode dynamic auto
```

---

## 2️⃣ أوضاع DTP

- **Dynamic Auto** → يستنى الطرف التاني يطلب Trunk.
    
- **Dynamic Desirable** → يحاول يتفاوض علشان يبقى Trunk.
    
- **Trunk** → بيجبر المنفذ يبقى Trunk ثابت.
    
- **Access** → بيجبر المنفذ يبقى Access ثابت.
    

---

## 3️⃣ تفعيل / تعطيل DTP

- **الوضع التلقائي (Default):**
    

```
switchport mode dynamic auto
```

- **إجبار المنفذ يبقى Trunk ثابت:**
    

```
switchport mode trunk
```

- **إجبار المنفذ يبقى Access ثابت:**
    

```
switchport mode access
```

- **إيقاف التفاوض (DTP Off):**
    

```
switchport nonegotiate
```

---

## 4️⃣ إيقاف DTP مع Trunk ثابت

```
Switch(config)# interface fa0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport nonegotiate
Switch(config-if)# end
```

---

## 5️⃣ جدول أوضاع DTP والتوافق بينهم

|منفذ 1 \ منفذ 2|Dynamic Auto|Dynamic Desirable|Trunk|Access|
|---|---|---|---|---|
|**Dynamic Auto**|❌ Access|✅ Trunk|✅ Trunk|❌ Access|
|**Dynamic Desirable**|✅ Trunk|✅ Trunk|✅ Trunk|❌ Access|
|**Trunk**|✅ Trunk|✅ Trunk|✅ Trunk|❌ No link|
|**Access**|❌ Access|❌ Access|❌ No link|✅ Access|

---

## ✅ ملاحظات للامتحان

- Dynamic Auto + Dynamic Auto = Access (لأن ولا واحد بيبادر).
    
- Dynamic Auto + Desirable = Trunk.
    
- Desirable + Desirable = Trunk.
    
- Trunk + أي وضع (ما عدا Access) = Trunk.
    
- Access + Trunk → بيعمل Mismatch ومش هيشتغل.
    
- Best Practice: **اقفل DTP** وخلي المنافذ ثابتة (Trunk أو Access).
    

---

### الشرح العملي 

![[2025-09-27 11-46-40.mkv]]