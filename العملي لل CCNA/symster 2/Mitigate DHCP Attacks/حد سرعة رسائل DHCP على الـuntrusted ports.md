
### 3) حد سرعة رسائل DHCP على الـuntrusted ports

الأمر (ممكن على كل بورت أو نطاق):

```
Switch(config)# interface range FastEthernet0/5 - 24
Switch(config-if-range)# ip dhcp snooping limit rate 6
```

**ليه؟** بيقلل احتمال هجوم DHCP starvation لأن البورت غير الموثوق مش هيقدر يولّد آلاف حزم في الثانية. القيمة `6` (packets/sec) شائعة لكن ممكن تزود/تنقص حسب الenvironment.

---
