
### 3. **أوامر التحقق (Verification Commands)**
بعد الإعداد، لازم تتأكد إن كل حاجة شغالة صح. الأوامر دي بتساعدك تشوف حالة الراوتر:
- ال`show ip interface brief`: بيوريك حالة الواجهات (IP ووضعها: up/down).
- ال`show running-config interface interface-type number`: بيوري إعدادات واجهة معينة.
- ال`show interfaces`: بيوري تفاصيل الواجهات (زي عدد الحزم المرسلة/المستقبلة).
- ال`show ip interface`: بيوري معلومات عن إعدادات IP للواجهات.
- ال`show ip route`: بيوري جدول التوجيه لـ IPv4.
- ال`ping`: بيختبر الاتصال بعنوان IP معين.
- **ملاحظة**: لو عايز فحص IPv6، استبدل `ip` بـ `ipv6` في الأوامر (مثل `show ipv6 route`).

---
