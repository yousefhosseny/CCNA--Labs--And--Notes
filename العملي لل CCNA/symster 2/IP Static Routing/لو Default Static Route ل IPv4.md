
- الأمر:
  ```bash
  ip route 0.0.0.0 0.0.0.0  ip-address  exit-intf
  ```
- **التفسير**:
  - `0.0.0.0 0.0.0.0`: يعني "كل الشبكات" (Quad-Zero Route)، لأن القناع /0 بيطابق أي عنوان.
  - ال`ip-address`: عنوان IP للراوتر التالي (Next-Hop).
  - ال`exit-intf`:  ال interface اللي هيخرج منه




