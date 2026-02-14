# 5) أوامر التحقق (show) وأين تشوف المشاكل

- تحقق أن DHCP snooping شغال ومرشّح على VLANs:
    
    ```
    Switch# show ip dhcp snooping
    ```
    
- شوف جدول الbindings:
    
    ```
    Switch# show ip dhcp snooping binding
    ```
    
- تحقق من حالة DAI وعدادات الـdrops:
    
    ```
    Switch# show ip arp inspection
    Switch# show ip arp inspection vlan 10
    ```
    
- شوف الـstatic/dynamic ip source bindings:
    
    ```
    Switch# show ip source binding
    ```
    
    أو (platform-specific) `show ip dhcp snooping database` لنسخ الـbinding من ملف database عند إعادة التشغيل. ([Cisco](https://www.cisco.com/c/en/us/td/docs/switches/lan/csbss/CBS220/CLI-Guide/b_220CLI/ip_dhcp_snooping_commands.pdf?utm_source=chatgpt.com "IP DHCP Snooping Commands"))
    
