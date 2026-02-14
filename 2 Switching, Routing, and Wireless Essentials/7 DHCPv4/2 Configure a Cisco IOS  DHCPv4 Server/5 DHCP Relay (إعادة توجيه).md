
### 5. **DHCP Relay (إعادة توجيه):**
- لو السيرفر DHCP موجود في شبكة تانية (مش نفس الشبكة بتاعة الأجهزة)، الراوتر لازم يبقى مظبوط كـ **Relay Agent** عشان ينقل طلبات الـ DHCP.
- الأمر: `ip helper-address address` (مثال: `ip helper-address 192.168.11.6`).
- الراوتر بياخد طلبات الـ DHCP (اللي هي Broadcast) ويحوّلها لـ Unicast ويبعتها للسيرفر.
- الـ `ip helper-address` مش بس لـ DHCP، بينقل خدمات تانية زي DNS و TFTP على منافذ معينة (زي Port 53 لـ DNS و Port 67/68 لـ DHCP).

![[Pasted image 20250908214702.png]]

