
### 6. **إعداد الروتينج مع OSPF**
- لو D1 متصل براوتر R1 في شبكة OSPF:
  1. **إعداد Routed Port**:
     ```
     D1(config)# interface g0/0/1
     D1(config-if)# no switchport
     D1(config-if)# ip address 10.10.10.2 255.255.255.0
     D1(config-if)# no shutdown
     ```
  2. **تفعيل الروتينج**:
     ```
     D1(config)# ip routing
     ```
  3. **إعداد OSPF** (بروتوكول روتينج ديناميكي):
     ```
     D1(config)# router ospf 1
     D1(config-router)# network 192.168.10.0 0.0.0.255 area 0
     D1(config-router)# network 192.168.20.0 0.0.0.255 area 0
     D1(config-router)# network 10.10.10.0 0.0.0.255 area 0
     D1(config-router)# end
     ```
  4. **فحص جدول الروتينج**:
     ```
     D1# show ip route
     ```
     (هيظهر الشبكات 192.168.10.0, 192.168.20.0, و10.10.10.0).
  5. **فحص الاتصال**:
     ```
     ping 10.20.20.x
     ```
     (للتأكد من الاتصال مع شبكات R1).

---



![[Pasted image 20250908212313.png]]

### الشرح للجزء  : من الدقيقه ال 00:00:00 الي الدقيقه  00:00:00