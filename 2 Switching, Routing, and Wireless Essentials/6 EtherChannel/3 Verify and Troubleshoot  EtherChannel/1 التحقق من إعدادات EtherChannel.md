
### 1. **التحقق من إعدادات EtherChannel**
بعد ما تعمل إعدادات EtherChannel، لازم تتأكد إنها شغالة صح باستخدام الأوامر دي:
- **`show interfaces port-channel`**: بيظهر الحالة العامة لواجهة الـ Port Channel (الرابط المنطقي).
- **`show etherchannel summary`**: بيظهر ملخص عن كل Port Channel (زي حالته وعدد المنافذ).
- **`show etherchannel port-channel`**: بيظهر تفاصيل عن واجهة Port Channel معينة.
- **`show interfaces etherchannel`**: بيديك معلومات عن دور كل منفذ فيزيائي في الـ EtherChannel.

---
