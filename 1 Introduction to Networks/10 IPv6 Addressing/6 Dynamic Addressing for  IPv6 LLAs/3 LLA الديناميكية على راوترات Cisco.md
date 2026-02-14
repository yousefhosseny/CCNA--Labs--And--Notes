
### 3. **LLA الديناميكية على راوترات Cisco**:
- راوترات Cisco بتولّد عنوان **LLA** تلقائيًا لما بنكوّن عنوان **GUA** على الواجهة.
- افتراضيًا، Cisco بتستخدم **EUI-64** لتوليد الـ Interface ID للـ LLA.
- مثال على واجهة `GigabitEthernet 0/0/0` في راوتر (R1):
  ```
  R1# show interface gigabitEthernet 0/0/0
  Hardware is ISR4221-2x1GE, address is 7079.b392.3640
  R1# show ipv6 interface brief
  GigabitEthernet0/0/0 [up/up]
  FE80::7279:B3FF:FE92:3640
  2001:DB8:ACAD:1::1
  ```
  - الـ LLA (`FE80::7279:B3FF:FE92:3640`) تم إنشاؤه باستخدام EUI-64 من عنوان MAC (`7079.b392.3640`).


![[Pasted image 20250808201841.png]]
