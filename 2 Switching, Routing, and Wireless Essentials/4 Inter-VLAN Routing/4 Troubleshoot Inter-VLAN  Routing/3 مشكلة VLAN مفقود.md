
### 3. **مشكلة: VLAN مفقود**
- **السبب**: ممكن الـ VLAN مش معمول إعداده، أو اتعمل له حذف بالغلط، أو مش مسموح بيه على رابط الترنك.
- **الأثر**: لو الـ VLAN اتشال، المنافذ المرتبطة بيه هتبقى غير نشطة (Inactive) لحد ما ترجّع الـ VLAN أو تربط المنافذ بـ VLAN تاني.
- **الحل**:
  1. أنشئ الـ VLAN لو مش موجود:
     ```
     S1(config)# vlan 10
     S1(config-vlan)# name FACULTY
     S1(config-vlan)# end
     ```
  2. تأكد إن المنفذ مربوط بالـ VLAN الصحيح:
     ```
     S1(config)# interface fa0/6
     S1(config-if)# switchport mode access
     S1(config-if)# switchport access vlan 10
     S1(config-if)# end
     ```
- **التحقق**:
  ```
  show vlan brief
  show interfaces fa0/6 switchport
  ```
  (بتأكد إن VLAN 10 موجود والمنفذ مربوط بيه).

---
### الشرح للجزء  : من الدقيقه ال 00:00:00 الي الدقيقه  00:00:00