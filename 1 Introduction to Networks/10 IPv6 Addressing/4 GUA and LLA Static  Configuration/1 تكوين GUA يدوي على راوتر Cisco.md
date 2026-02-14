
### 1. **تكوين GUA يدوي على راوتر Cisco**:
- أوامر تكوين IPv6 على راوتر Cisco مشابهة لأوامر IPv4، بس بنستبدل كلمة `ip` بـ `ipv6` في الأوامر.
- لتكوين عنوان **GUA** على واجهة الراوتر، نستخدم الأمر:
  ```
  ipv6 address <عنوان IPv6>/<طول الـ Prefix>
  ```
- مثال لتكوين GUA على واجهة `GigabitEthernet 0/0/0` في راوتر (R1):
  ```
  R1(config)# interface gigabitethernet 0/0/0
  R1(config-if)# ipv6 address 2001:db8:acad:1::1/64
  R1(config-if)# no shutdown
  R1(config-if)# exit
  ```
- الشرح:
  - بنختار الواجهة (`GigabitEthernet 0/0/0`).
  - بنحدد عنوان GUA (`2001:db8:acad:1::1`) مع طول الـ Prefix (`/64`).
  - `no shutdown` بيفَعّل الواجهة.

![[Pasted image 20250808201449.png]]