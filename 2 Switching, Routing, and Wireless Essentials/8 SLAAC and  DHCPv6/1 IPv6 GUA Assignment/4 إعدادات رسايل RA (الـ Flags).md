
### 4. **إعدادات رسايل RA (الـ Flags)**
رسايل **RA** فيها 3 إعدادات (Flags) بتحدد طريقة أخذ العنوان:
- **A Flag (Address Autoconfiguration):** لو مفعّل، الجهاز بيستخدم **SLAAC** (Stateless Address Autoconfiguration) عشان يولّد عنوان GUA بنفسه بناءً على الـ Prefix اللي بيبعتها الراوتر.
- **O Flag (Other Configuration):** لو مفعّل، يعني الجهاز ممكن ياخد إعدادات إضافية (زي DNS) من سيرفر DHCPv6 بدون حالة (Stateless DHCPv6).
- **M Flag (Managed Address Configuration):** لو مفعّل، الجهاز بياخد عنوان GUA وإعدادات من سيرفر DHCPv6 بحالة (Stateful DHCPv6).
- الراوتر بيبعت الـ RA مع الـ Flags دي، والجهاز بيقرر بناءً عليها إزاي ياخد العنوان (لكن القرار النهائي بيكون عند الجهاز).


![[Pasted image 20250908214939.png]]
