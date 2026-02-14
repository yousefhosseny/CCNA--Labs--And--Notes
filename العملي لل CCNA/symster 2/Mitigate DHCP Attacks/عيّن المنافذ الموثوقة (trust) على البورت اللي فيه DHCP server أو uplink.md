
### 4) عيّن المنافذ الموثوقة (trust) على البورت اللي فيه DHCP server أو uplink

الأمر على انفِرْفِيس السِرڤِر أو uplink:

```
Switch(config)# interface FastEthernet0/2
Switch(config-if)# ip dhcp snooping trust
```

**ليه؟** لأن رسائل الـDHCPOFFER / DHCPACK **تأتي من الـserver**؛ لو البورت الراجع منه السيرفر موجود كـuntrusted فهتتلغى الردود الشرعية والـclients مش هياخدوا عناوين. أي بورت يصل منه DHCP server أو route-relay (رابط لسويتش تاني / راوتر مع DHCP relay) لازم يكون trusted.

---
