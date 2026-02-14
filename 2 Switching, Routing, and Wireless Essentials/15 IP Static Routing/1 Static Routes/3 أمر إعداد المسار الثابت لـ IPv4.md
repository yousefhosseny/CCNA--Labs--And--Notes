
### 3. **أمر إعداد المسار الثابت لـ IPv4**
- الأمر:
  ```bash
  ip route network-address subnet-mask  ip-address   exit-intf     [distance]
  ```
- **التفسير**:
  - ال`network-address`: عنوان الشبكة الوجهة (مثل 192.168.1.0).
  - ال`subnet-mask`: قناع الشبكة (مثل 255.255.255.0).
  - ال`ip-address`: عنوان IP للراوتر التالي (Next-Hop).
  - ال`exit-intf`: واجهة الخروج (مثل Serial0/1/0).
  - ال`distance`: الـ Administrative Distance (اختياري، القيمة الافتراضية 1).
- لازم تختار إما `ip-address` أو `exit-intf` أو الاتنين.

---
