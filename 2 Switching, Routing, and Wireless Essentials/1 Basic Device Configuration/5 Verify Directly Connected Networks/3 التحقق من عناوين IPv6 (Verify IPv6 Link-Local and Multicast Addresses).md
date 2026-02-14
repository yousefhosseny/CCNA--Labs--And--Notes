
### **3. التحقق من عناوين IPv6 (Verify IPv6 Link-Local and Multicast Addresses):**
- عند تكوين عنوان IPv6 على واجهة، يتم إضافة عنوانين تلقائيًا:
  1. **عنوان Global Unicast**: العنوان الذي تُعيّنه يدويًا (مثل 2001:db8:acad:1::1/64).
  2. **عنوان Link-Local**: يبدأ بـ **FE80** ويُضاف تلقائيًا لكل واجهة لها عنوان Global Unicast.
- **الأمر `show ipv6 interface gigabitethernet 0/0/0`:**
  - يعرض تفاصيل الواجهة، بما في ذلك:
    - عنوان Link-Local.
    - عناوين Multicast (تبدأ بـ **FF02**) المرتبطة بالواجهة.
- **ملاحظة:** عنوان Link-Local مطلوب دائمًا لتفعيل واجهة IPv6، لكن عنوان Global Unicast اختياري.

---

![[Pasted image 20250823032757.png]]
