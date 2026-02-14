
## 4) تعطيل DTP على منافذ الـ trunk (`switchport nonegotiate`)

**ليه؟**  
حتى الـ trunk لو اتترك يتفاوض، الطرف التاني ممكن يخدع أو يضغط ليعمل trunk غير مقصود. تعطيل التفاوض يمنع إرسال/استقبال إطارات DTP.

**أمر:**

```shell
interface GigabitEthernet0/48
  switchport nonegotiate
  switchport mode trunk
```

**تأكيد/فحص:**

```shell
show interfaces GigabitEthernet0/48 switchport
# راجع: Negotiation of Trunking: Off
show interfaces trunk
```

**تحذير عملي:** لو استخدمت `nonegotiate`، لازم الطرف التاني مهيأ يدوياً كمان (mode trunk) لأن `nonegotiate` يمنع الـ DTP وبالتالي لو الطرف التاني كان على dynamic ممكن ما يحصلش trunk.

---
