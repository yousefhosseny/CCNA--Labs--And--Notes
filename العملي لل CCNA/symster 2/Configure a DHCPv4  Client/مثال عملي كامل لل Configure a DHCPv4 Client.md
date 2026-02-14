
## 🎯 السيناريو

- عندك راوتر متوصل بالـ ISP.
    
- الراوتر محتاج ياخد عنوان IP على واجهة **G0/0/1** من سيرفر DHCP (عند الـ ISP).
    
- بعد كده هنتأكد إن الواجهة اشتغلت وخدت IP.
    

---

## 🛠️ خطوات التنفيذ

### 1. ندخل على الراوتر

```bash
Router> enable
Router#
```

---

### 2. ندخل على وضع الإعدادات

```bash
Router# configure terminal
Router(config)#
```

---

### 3. نضبط الواجهة كـ DHCP Client

نفترض إن الواجهة اللي رايحة للـ ISP هي `G0/0/1`:

```bash
Router(config)# interface g0/0/1
Router(config-if)# ip address dhcp
Router(config-if)# no shutdown
```

✅ هنا الراوتر بقى يبعث رسائل DHCP (Discover → Offer → Request → ACK) عشان ياخد IP.

---

### 4. التأكد من إن الواجهة خدت IP

```bash
Router# show ip interface brief
```

📌 مثال على النتيجة:

```
Interface              IP-Address      OK? Method Status                Protocol
GigabitEthernet0/0/0   unassigned      YES unset  administratively down down
GigabitEthernet0/0/1   209.165.201.12  YES DHCP   up                    up
```

- باين إن `G0/0/1` أخذت IP: `209.165.201.12` بالطريقة DHCP.
    
- كلمة **Method = DHCP** معناها إن العنوان جه من DHCP Server.
    

---

### 5. التأكد من إعدادات DHCP على الواجهة

```bash
Router# show running-config
```

📌 هتلاقي:

```
interface GigabitEthernet0/0/1
 ip address dhcp
 no shutdown
```

---

### 6. (اختياري) تتأكد من معلومات DHCP المستلمة

```bash
Router# show dhcp lease
```

📌 مثال على النتيجة:

```
Temp IP addr: 209.165.201.12 for peer on Interface: GigabitEthernet0/0/1
DHCP Lease server: 209.165.201.1, state: 3 Bound
Lease: 86400 seconds, Renewal: 43200 seconds, Rebind: 75600 seconds
```

- هنا واضح الـ IP اللي استلمه، السيرفر اللي وزعه، ومدة التجديد (lease time).
    

---

## ✅ الخلاصة

- ضبطنا الواجهة كـ DHCP Client باستخدام:
    
    ```bash
    ip address dhcp
    no shutdown
    ```
    
- تأكدنا إن الواجهة خدت IP من DHCP Server.
    
- شفنا إعدادات الـ DHCP Lease اللي اتخدت من الـ ISP.
    

---
