
### **1. إعدادات الراوتر الأساسية (Basic Router Settings):**
- الراوترات والمحولات (Switches) من Cisco متشابهة في نظام التشغيل (IOS) وبعض الأوامر.
- هناك خطوات أساسية يجب تنفيذها عند إعداد أي راوتر:
  1. **تسمية الراوتر (Hostname):** لتمييزه عن غيره من الأجهزة.
     ```bash
     Router# configure terminal
     Router(config)# hostname R1
     ```
  2. **إعداد كلمات المرور:** لحماية الوصول إلى الراوتر.
     - كلمة مرور للوضع Privileged EXEC:
       ```bash
       R1(config)# enable secret cisco
       ```
     - كلمة مرور لخطوط VTY (للوصول عن بُعد):
       ```bash
       R1(config)# line vty 0 4
       R1(config-line)# password cisco
       R1(config-line)# login
       R1(config-line)# end
       ```
  3. **إعداد رسالة تحذير (Banner):** لإعلام المستخدمين بأن الوصول غير المصرح به ممنوع.
     ```bash
     R1(config)# banner motd #Unauthorized access is prohibited!#
     ```
  4. **حفظ الإعدادات:** لضمان عدم فقدانها عند إعادة تشغيل الراوتر.
     ```bash
     R1# copy running-config startup-config
     ```

---

![[Pasted image 20250823032635.png]]
