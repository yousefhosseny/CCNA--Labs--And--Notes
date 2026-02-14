
### 1. **رسائل RS وRA**:
- **RS (Router Solicitation)**: الأجهزة بتبعت الرسالة دي عشان تكتشف الراوترات اللي تدعم IPv6 في الشبكة.
- **RA (Router Advertisement)**: الراوتر بيرد برسالة RA عشان يقول للأجهزة إزاي تحصل على عنوان GUA، وكمان بيديهم معلومات زي:
  - الـ **Prefix** وطوله (جزء الشبكة).
  - عنوان **Default Gateway**.
  - عناوين **DNS** واسم النطاق (Domain Name).
- الـ RA بتقترح واحدة من 3 طرق لتكوين GUA:
  1. **SLAAC** (Stateless Address Autoconfiguration).
  2. **SLAAC مع Stateless DHCPv6**.
  3. **Stateful DHCPv6** (بدون SLAAC).
