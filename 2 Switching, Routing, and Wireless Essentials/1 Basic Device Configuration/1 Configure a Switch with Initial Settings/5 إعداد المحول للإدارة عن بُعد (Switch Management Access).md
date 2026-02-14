
### **5. إعداد المحول للإدارة عن بُعد (Switch Management Access):**
لإدارة المحول عن بُعد، يجب إعداد واجهة إدارية (SVI) مع عنوان IP:
- الواجهة الافتراضية هي **VLAN 1**، لكن يُفضل استخدام VLAN آخر (مثل VLAN 99) للأمان.
- خطوات الإعداد:
  1. **إعداد عنوان IP لواجهة SVI:**
     ```bash
     S1# configure terminal
     S1(config)# interface vlan 99
     S1(config-if)# ip address 172.17.99.11 255.255.255.0
     S1(config-if)# no shutdown
     S1(config-if)# end
     ```
  2. **إعداد البوابة الافتراضية (Default Gateway):**
     ```bash
     S1# configure terminal
     S1(config)# ip default-gateway 172.17.99.1
     S1(config)# end
     ```
  3. **حفظ الإعدادات:**
     ```bash
     S1# copy running-config startup-config
     ```
  4. **التحقق من الإعدادات:**
     - استخدم الأوامر:
       ```bash
       show ip interface brief
       show ipv6 interface brief
       ```
     - تُظهر هذه الأوامر حالة الواجهات وعناوين IP.

- **ملاحظات:**
  - عنوان IP المُعين لواجهة SVI مخصص للإدارة عن بُعد فقط، وليس لتوجيه الحزم (Routing).
  - لدعم IPv6، قد تحتاج إلى تفعيل وضع IPv4 وIPv6 باستخدام:
    ```bash
    sdm prefer dual-ipv4-and-ipv6 default
    ```
    ثم إعادة تشغيل المحول.

---

![[Pasted image 20250823032108.png]]


![[Pasted image 20250823032214.png]]
