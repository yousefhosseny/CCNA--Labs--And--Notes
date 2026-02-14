
يوجد طريقتين شائعتين حسب الحاجة والإصدار:

**أ) حجز عن طريق client identifier أو host**

```text
Router(config)# ip dhcp pool PRINTER1
Router(dhcp-config)# host 192.168.1.50 255.255.255.0
Router(dhcp-config)# client-identifier 0100.1f16.18df.ec
Router(dhcp-config)# default-router 192.168.1.1
```

(تستخدم `client-identifier` لو العميل يرسل Client-ID مختلف عن الـ MAC — الراوتر ممكن يطبع الـ client-id في الـ debug لتعرفه). ([Cisco](https://www.cisco.com/c/en/us/td/docs/ios/12_2sb/12_2sba/feature/guide/sbhcpsm.html?utm_source=chatgpt.com "DHCP - Static Mapping"))

**ب) حجز عن طريق MAC (hardware address)**

```text
Router(config)# ip dhcp pool PRINTER2
Router(dhcp-config)# address 192.168.1.60 hardware-address 0011.2233.4455
Router(dhcp-config)# default-router 192.168.1.1
```

(بعض IOSs يقبل أيضاً `host` بدل `address`؛ لكن الفكرة: تربط IP بمعرف العميل). ([mrn-cciew](https://mrncciew.com/2013/06/10/ios-dhcp-add-reservation/?utm_source=chatgpt.com "IOS DHCP Add. Reservation"))

---
