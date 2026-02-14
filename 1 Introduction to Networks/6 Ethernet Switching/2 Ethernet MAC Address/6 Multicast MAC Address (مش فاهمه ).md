##### **Multicast MAC Address**
- الـ **Multicast MAC Address** بيستخدم عشان يبعت إطار لمجموعة معينة من الأجهزة (مش جهاز واحد ولا الكل).
- مواصفاته:
  - لو البيانات IPv4 Multicast، الـ Destination MAC Address بيبدأ بـ **01-00-5E**.
  - لو IPv6 Multicast، بيبدأ بـ **33-33**.
  - فيه عناوين Multicast محجوزة لبروتوكولات تانية (زي **Spanning Tree Protocol - STP**).
  - زي الـ Broadcast، الإطار بيترسل لكل منافذ السويتش (ما عدا المنفذ اللي جاله منه)، بس لو السويتش بيدعم **Multicast Snooping**، بيبعت الإطار بس للأجهزة اللي في المجموعة.
  - الراوتر ما بيمررش الـ Multicast إلا لو معمول له تهيئة خاصة لتوصيل حزم Multicast.
- الـ Multicast Address بيستخدم بس كـ Destination (مش Source)، لأنه بيمثل مجموعة أجهزة (Host Group).
- زي الـ Broadcast، لازم يكون فيه عنوان MAC Multicast مطابق لعنوان IP Multicast.

---
![[Pasted image 20250715203607.png]]
