لو السيرفر في شبكة تانية لازم الـ router/svi اللي بيستقبل البوّت برودكاست يعمل relay باستخدام:

```text
Router(config)# interface GigabitEthernet0/1.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 192.168.10.1 255.255.255.0
Router(config-subif)# ip helper-address 192.168.11.6
```

`ip helper-address` بيحوّل البث لـ unicast للسيرفر وبافتراض الافتراضات يقدّم تحويل لعدة خدمات UDP (منها DHCP / BOOTP). المنافذ التي تُعاد توجيهها افتراضياً تشمل: **Time (37), DNS (53), BOOTP/DHCP (67,68), TFTP (69), NetBIOS (137,138)** وغيره حسب النسخة. فتأكد من فتح الجدار الناري بين الشبكات. ([Cisco](https://www.cisco.com/c/en/us/td/docs/routers/ios/config/17-x/ip-addressing/b-ip-addressing/m_iap-bph-0.html?utm_source=chatgpt.com "IP Addressing Configuration Guide, Cisco IOS XE 17.x"))

---
