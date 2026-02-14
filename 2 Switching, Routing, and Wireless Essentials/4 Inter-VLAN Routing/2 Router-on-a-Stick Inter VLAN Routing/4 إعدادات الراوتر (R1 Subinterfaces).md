
### 4. **إعدادات الراوتر (R1 Subinterfaces)**
- الراوتر بيستخدم منفذ واحد (G0/0/1) مقسم لـ **Subinterfaces** عشان ينقل بيانات VLANs مختلفة.
- خطوات إعداد الـ Subinterfaces:
  1. ادخل وضع الـ Global Configuration:
     ```
     R1# configure terminal
     ```
  2. إنشاء Subinterface لكل VLAN:
     - لـ VLAN 10:
       ```
       R1(config)# interface g0/0/1.10
       R1(config-subif)# encapsulation dot1q 10
       R1(config-subif)# ip address 192.168.10.1 255.255.255.0
       ```
     - لـ VLAN 20:
       ```
       R1(config)# interface g0/0/1.20
       R1(config-subif)# encapsulation dot1q 20
       R1(config-subif)# ip address 192.168.20.1 255.255.255.0
       ```
     - لـ VLAN 99 (Native VLAN):
       ```
       R1(config)# interface g0/0/1.99
       R1(config-subif)# encapsulation dot1q 99 native
       R1(config-subif)# ip address 192.168.99.1 255.255.255.0
       ```
  3. تفعيل المنفذ الرئيسي:
     ```
     R1(config)# interface g0/0/1
     R1(config-if)# no shutdown
     R1(config-if)# end
     ```
- **ملاحظات**:
  - الأمر `encapsulation dot1q [vlan-id]` بيخلي الـ Subinterface يتعامل مع بيانات الـ VLAN الموسومة بـ 802.1Q.
  - كلمة `native` بتستخدم لو عايز تحدد الـ Native VLAN (اللي مابتتوسمش).
  - كل Subinterface لازم يكون عنده عنوان IP في Subnet مختلف عشان يبقى الـ Default Gateway للـ VLAN.

---
### الشرح للجزء  : من الدقيقه ال 02:36:37 الي الدقيقه  00:00:00