- الأمر:
  ```bash
  ipv6 route ::/0 ipv6-address  exit-intf
  ```
- **التفسير**:
  - `::/0`: يعني "كل الشبكات"، لأن الـ Prefix /0 بيطابق أي عنوان IPv6.
 - ال`ipv6-address`: عنوان IP للراوتر التالي (Next-Hop).
  - ال`exit-intf`:  ال interface اللي هيخرج منه