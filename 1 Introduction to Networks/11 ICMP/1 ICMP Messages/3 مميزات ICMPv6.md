3. **مميزات ICMPv6**:
   - فيه بروتوكولات إضافية ضمن **Neighbor Discovery Protocol (NDP)**، زي:
     - **Router Solicitation (RS)** و**Router Advertisement (RA)**:
       - الأجهزة بتبعت RS عشان تسأل عن معلومات الشبكة، والراوتر يرد بـ RA فيها تفاصيل زي عنوان الـ IPv6، الـ prefix، وعنوان الـ DNS.
       - لو الجهاز بيستخدم **SLAAC** (Stateless Address Autoconfiguration)، بياخد عنوان الراوتر كـ default gateway.
     - **Neighbor Solicitation (NS)** و**Neighbor Advertisement (NA)**:
       - بيستخدموا للتحقق من عنوان IPv6 (Duplicate Address Detection - DAD) عشان يتأكدوا إنه فريد، وكمان لمعرفة عنوان MAC الخاص بجهاز معين.

