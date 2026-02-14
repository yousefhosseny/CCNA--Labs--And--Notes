### **4. إعداد SSH على المحول:**
لإعداد SSH على محول Cisco Catalyst 2960، اتبع هذه الخطوات:

1. **التحقق من دعم SSH:**
   - استخدم الأمر:
     ```bash
     show ip ssh
     ```
   - إذا لم يتعرف المحول على الأمر، فهذا يعني أن IOS لا يدعم التشفير.

2. **إعداد اسم النطاق (Domain Name):**
   - حدد اسم نطاق للشبكة:
     ```bash
     S1# configure terminal
     S1(config)# ip domain-name example.com
     ```

3. **إنشاء مفتاح RSA:**
   - هذا المفتاح يُمكّن SSH تلقائيًا:
     ```bash
     S1(config)# crypto key generate rsa
     ```
   - اختر طول المفتاح (يفضل 1024 بت أو أكثر).
   - **ملاحظة:** إذا أردت حذف المفتاح، استخدم:
     ```bash
     crypto key zeroize rsa
     ```

4. **إعداد المصادقة المحلية:**
   - أنشئ اسم مستخدم وكلمة مرور:
     ```bash
     S1(config)# username admin secret ccna
     ```

5. **إعداد خطوط VTY (Virtual Terminal Lines):**
   - قم بتفعيل SSH على خطوط VTY:
     ```bash
     S1(config)# line vty 0 15
     S1(config-line)# transport input ssh
     S1(config-line)# login local
     S1(config-line)# end
     ```

6. **تفعيل SSH الإصدار 2:**
   - بشكل افتراضي، SSH يدعم الإصدارين 1 و2، لكن يُفضل استخدام الإصدار 2 فقط:
     ```bash
     S1(config)# ip ssh version 2
     ```

7. **حفظ الإعدادات:**
   - احفظ التغييرات:
     ```bash
     S1# copy running-config startup-config
     ```

---

![[Pasted image 20250823032615.png]]
