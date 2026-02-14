
### 2. **مسار ثابت باستخدام عنوان الـ Next-Hop (IPv6 Next-Hop Static Route)**
- نفس الفكرة لـ IPv6، بس لازم تفعّل توجيه IPv6 أولًا.
- **مثال على R1**:
  ```bash
  ipv6 unicast-routing
  ipv6 route 2001:db8:acad:1::/64 2001:db8:acad:2::2
  ipv6 route 2001:db8:cafe:1::/64 2001:db8:acad:2::2
  ipv6 route 2001:db8:cafe:2::/64 2001:db8:acad:2::2
  ```
- **التفسير**:
  - `ipv6 unicast-routing`: تفعيل توجيه IPv6.
  - كل أمر بيحدد شبكة وجهة (مثل 2001:db8:acad:1::/64) وعنوان الـ Next-Hop (2001:db8:acad:2::2، وهو عنوان R2).
  - المسارات دي بتتضاف لجدول التوجيه لـ IPv6.

---

![[Pasted image 20250908222012.png]]
