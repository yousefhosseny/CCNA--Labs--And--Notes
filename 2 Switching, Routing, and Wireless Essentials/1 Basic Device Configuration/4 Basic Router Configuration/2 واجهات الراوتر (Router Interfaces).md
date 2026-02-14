
### **2. واجهات الراوتر (Router Interfaces):**
- الراوترات تدعم شبكات LAN (مثل Ethernet) وWAN (مثل Serial، DSL).
- **أنواع الواجهات في الراوترات:**
  - واجهات Gigabit Ethernet مدمجة.
  - فتحات HWIC لدعم واجهات إضافية (مثل Serial أو DSL).
- **خطوات إعداد واجهة:**
  1. **إعداد عنوان IP:**
     - يجب تخصيص عنوان IP (IPv4 أو IPv6) لكل واجهة.
     - مثال لـ IPv4:
       ```bash
       R1(config)# interface GigabitEthernet 0/0
       R1(config-if)# ip address 192.168.1.1 255.255.255.0
       ```
     - مثال لـ IPv6:
       ```bash
       R1(config-if)# ipv6 address 2001:db8:acad:1::1/64
       ```
  2. **تفعيل الواجهة:**
     - الواجهات تكون معطلة افتراضيًا (Shutdown). لتفعيلها:
       ```bash
       R1(config-if)# no shutdown
       ```
     - يجب أن تكون الواجهة متصلة بجهاز آخر (مثل محول أو راوتر) لتصبح نشطة.
  3. **إضافة وصف (Description) - اختياري:**
     - يُفضل إضافة وصف للواجهة لتسهيل استكشاف الأخطاء.
       ```bash
       R1(config-if)# description Link to LAN1
       ```

---

