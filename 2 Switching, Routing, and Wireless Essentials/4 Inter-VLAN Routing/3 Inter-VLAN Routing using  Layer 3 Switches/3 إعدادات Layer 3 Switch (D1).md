
### 3. **إعدادات Layer 3 Switch (D1)**
عشان نعمل Inter-VLAN Routing على الـ Layer 3 Switch، بنتبع الخطوات دي:
1. **إنشاء الـ VLANs**:
   ```
   D1# configure terminal
   D1(config)# vlan 10
   D1(config-vlan)# name FACULTY
   D1(config)# vlan 20
   D1(config-vlan)# name STUDENTS
   D1(config-vlan)# end
   ```
2. **إنشاء واجهات SVI لكل VLAN**:
   - كل SVI بتاخد عنوان IP يبقى الـ Default Gateway للـ VLAN.
   ```
   D1(config)# interface vlan 10
   D1(config-if)# ip address 192.168.10.1 255.255.255.0
   D1(config-if)# no shutdown
   D1(config)# interface vlan 20
   D1(config-if)# ip address 192.168.20.1 255.255.255.0
   D1(config-if)# no shutdown
   D1(config-if)# end
   ```
3. **إعداد منافذ الأكسس (Access Ports)**:
   - ربط منافذ الأجهزة (زي PC1 وPC2) بالـ VLANs المناسبة:
   ```
   D1(config)# interface fa0/6
   D1(config-if)# switchport mode access
   D1(config-if)# switchport access vlan 10
   D1(config)# interface fa0/18
   D1(config-if)# switchport mode access
   D1(config-if)# switchport access vlan 20
   D1(config-if)# end
   ```
4. **تفعيل الروتينج**:
   - لازم تفعّل الروتينج على السويتش بأمر:
   ```
   D1(config)# ip routing
   D1(config)# end
   ```
   - ده الأمر اللي بيخلي السويتش ينقل البيانات بين VLAN 10 وVLAN 20.

---


### الشرح للجزء  : من الدقيقه ال 00:00:00 الي الدقيقه  00:00:00