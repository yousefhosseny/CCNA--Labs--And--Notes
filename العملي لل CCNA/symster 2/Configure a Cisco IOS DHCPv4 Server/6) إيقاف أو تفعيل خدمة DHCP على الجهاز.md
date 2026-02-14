- لتعطيل الخدمة ككل (نادر الاستخدام):
    
    ```
    Router(config)# no service dhcp
    ```
    
- لإعادة التفعيل:
    
    ```
    Router(config)# service dhcp
    ```
    

ملاحظة: تعطيل الخدمة أو حذف Pools ممكن يؤدي لحالات مؤقتة من ازدواجية عناوين لدى العملاء حتى تنتهي الـ leases. ([Cisco](https://www.cisco.com/en/US/docs/ios/12_4t/ip_addr/configuration/guide/htdhcpsv.html?utm_source=chatgpt.com "Configuring the Cisco IOS DHCP Server [Support]"))

---
