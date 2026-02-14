
#### 3. **ضبط واجهة السويتش الافتراضية (Switch Virtual Interface Configuration):**
- عشان تتحكم في سويتش Cisco عن بُعد (مثل عبر SSH أو Telnet)، لازم تضبط عنوان IP على **واجهة VLAN الافتراضية (SVI)**.
- **الخطوات:**
  1. ادخل وضع Global Configuration:
     ```
     configure terminal
     ```
  2. ادخل واجهة VLAN 1:
     ```
     interface vlan 1
     ```
  3. اضبط عنوان IP وSubnet Mask:
     ```
     ip address [عنوان IP] [Subnet Mask]
     ```
     مثال: `ip address 192.168.1.2 255.255.255.0`
  4. فعّل الواجهة:
     ```
     no shutdown
     ```

---

![[Pasted image 20250718173009.png]]
