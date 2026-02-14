
### 3. **تكوين LLA يدوي على راوتر**:
- تكوين عنوان **LLA** يدويًا بيخلينا نختار عنوان سهل التذكر ومميز.
- الأمر المستخدم هو:
  ```
  ipv6 address <عنوان LLA> link-local
  ```
- مثال لتكوين LLA على واجهة `GigabitEthernet 0/0/0` في راوتر (R1):
  ```
  R1(config)# interface gigabitethernet 0/0/0
  R1(config-if)# ipv6 address fe80::1:1 link-local
  R1(config-if)# no shutdown
  R1(config-if)# exit
  ```
- الشرح:
  - بنختار الواجهة.
  - بنحدد عنوان LLA (مثلاً `fe80::1:1`) مع كلمة `link-local` عشان نحدد إنه عنوان محلي.
  - `no shutdown` بيفَعّل الواجهة.
- ملاحظة:
  - عنوان LLA لازم يكون فريد داخل الشبكة المحلية (Link).
  - عادةً بنستخدم LLA مختلف لكل واجهة في الراوتر عشان يسهل تمييز الراوتر والواجهة.



![[Pasted image 20250808201528.png]]

