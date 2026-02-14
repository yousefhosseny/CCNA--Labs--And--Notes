
### 2. **أوامر الإعداد (Configuration Commands)**
الأوامر دي بتستخدم لإعداد راوتر اسمه **R1**، وبتشمل إعدادات أساسية زي الاسم، كلمات المرور، واجهات الشبكة، ودعم IPv4 وIPv6. هنا الخطوات بشكل مبسط:

1. **دخول وضع الإعداد**:
   - `enable`: ادخل وضع الـ Privileged EXEC.
   - `configure terminal`: ادخل وضع الإعداد العام (Global Configuration).

2. **تغيير اسم الراوتر**:
   - `hostname R1`: سمّي الراوتر R1.

3. **إعداد كلمة مرور مشفرة**:
   - `enable secret class`: ضبط كلمة مرور مشفرة (class) للدخول لوضع الـ Privileged EXEC.

4. **إعداد واجهة الـ Console**:
   - `line console 0`: ادخل إعدادات منفذ الـ Console.
   - `logging synchronous`: خلّي الرسائل ما تقاطعش كتابتك.
   - `password cisco`: ضبط كلمة مرور (cisco) للـ Console.
   - `login`: تفعيل طلب كلمة المرور.

5. **إعداد واجهة الـ VTY (للتحكم عن بُعد)**:
   - `line vty 0 4`: إعداد خطوط VTY من 0 لـ 4 (للوصول عن طريق Telnet أو SSH).
   - `password cisco`: ضبط كلمة مرور (cisco).
   - `login`: تفعيل طلب كلمة المرور.
   - `transport input ssh telnet`: السماح بالوصول عبر SSH وTelnet.

6. **تشفير كلمات المرور**:
   - `service password-encryption`: تشفير كل كلمات المرور في الإعدادات.

7. **إعداد رسالة تحذير (Banner)**:
   - `banner motd #`: إعداد رسالة تحذير تظهر لما حد يحاول يدخل الراوتر، زي "Unauthorized access is prohibited!".

8. **تفعيل توجيه IPv6**:
   - `ipv6 unicast-routing`: تفعيل دعم توجيه IPv6.

9. **إعداد الواجهات (Interfaces)**:
   - **واجهة GigabitEthernet 0/0/0 (متصلة بشبكة LAN 1)**:
     - `description Link to LAN 1`: وصف الواجهة.
     - `ip address 10.0.1.1 255.255.255.0`: ضبط عنوان IPv4.
     - `ipv6 address 2001:db8:acad:1::1/64`: ضبط عنوان IPv6.
     - `ipv6 address fe80::1:a link-local`: ضبط عنوان IPv6 محلي.
     - `no shutdown`: تفعيل الواجهة.
   - **واجهة GigabitEthernet 0/0/1 (متصلة بشبكة LAN 2)**:
     - نفس الإعدادات بس بعناوين مختلفة (IPv4: 10.0.2.1, IPv6: 2001:db8:acad:2::1/64).
   - **واجهة Serial 0/1/1 (متصلة براوتر R2)**:
     - نفس الإعدادات بس بعناوين مختلفة (IPv4: 10.0.3.1, IPv6: 2001:db8:acad:3::1/64).

10. **حفظ الإعدادات**:
    - `copy running-config startup-config`: حفظ الإعدادات عشان ما تتمسحش لما الراوتر يترست.

---
