### شرح القسم بأبسط طريقة ممكنة:

القسم ده بيتكلم عن **كيفية تهيئة واجهات الروتر** في Cisco وازاي تتحقق من إعداداتها باستخدام أوامر التحقق. هنا الشرح بطريقة مبسطة:

---

#### 1. **تهيئة واجهات الروتر (Configure Router Interfaces):**
- عشان الروتر يشتغل في الشبكة، لازم تظبط واجهاته (Interfaces) اللي هي النقاط اللي بيتصل من خلالها بالشبكات.
- **الأوامر الأساسية لتهيئة واجهة:**
  1. ادخل وضع الواجهة:
     ```
     interface [نوع-ورقم]
     ```
     مثال: `interface gigabitEthernet 0/0/0`
  2. أضف وصف (اختياري، بس مفيد للتوثيق):
     ```
     description [نص الوصف]
     ```
     مثال: `description Link to LAN`
  3. اضبط عنوان IPv4:
     ```
     ip address [عنوان IPv4] [Subnet Mask]
     ```
     مثال: `ip address 192.168.10.1 255.255.255.0`
  4. اضبط عنوان IPv6 (لو بتستخدم IPv6):
     ```
     ipv6 address [عنوان IPv6]/[طول القناع]
     ```
     مثال: `ipv6 address 2001:db8:acad:10::1/64`
  5. فعّل الواجهة:
     ```
     no shutdown
     ```
     (ده بيخلي الواجهة تشتغل).

- **مثال عملي (لواجهة G0/0/0):**
  ```
  interface gigabitEthernet 0/0/0
  description Link to LAN
  ip address 192.168.10.1 255.255.255.0
  ipv6 address 2001:db8:acad:10::1/64
  no shutdown
  exit
  ```

- **مثال آخر (لواجهة G0/0/1):**
  ```
  interface gigabitEthernet 0/0/1
  description Link to R2
  ip address 209.165.200.225 255.255.255.252
  ipv6 address 2001:db8:feed:224::1/64
  no shutdown
  exit
  ```

- **ملاحظات:**
  - الوصف (`description`) بيساعدك تعرف الواجهة متصلة بإيه.
  - أمر `no shutdown` ضروري عشان الواجهة تشتغل، وإلا هتفضل معطلة.

---
1
![[Pasted image 20250718232332.png]]

2
![[Pasted image 20250718232406.png]]


