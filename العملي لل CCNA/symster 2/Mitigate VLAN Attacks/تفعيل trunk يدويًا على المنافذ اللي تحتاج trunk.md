
## 3) تفعيل trunk يدويًا على المنافذ اللي تحتاج trunk

**ليه؟**  
عدم الاعتماد على التفاوض التلقائي — خليك متحكم بنفسك في أي منافذ تبقى trunk، واكتفي بالمنافذ اللي بتوصل لسويتشات تانية أو للسيرفرات اللي محتاجة trunk.

**أوامر نموذجية:**

```shell
interface GigabitEthernet0/48
  description Uplink_to_Core
  switchport trunk encapsulation dot1q   ! (لو السويتش يدعم الاختيار)
  switchport mode trunk
  switchport trunk allowed vlan 10,20,30
  switchport trunk native vlan 99
exit
```

**تأكيد/فحص:**

```shell
show interfaces trunk
show interfaces GigabitEthernet0/48 switchport
# راجع: "Administrative Mode: trunk" و "Operational Mode: trunk"
show vlan brief
```

**ملاحظة:** استخدم `switchport trunk allowed vlan` بدلاً من السماح بكل الـ VLANs — ده يمنع مرور VLANs غير ضرورية.

---
