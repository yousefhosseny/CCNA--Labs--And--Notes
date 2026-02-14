

1. **فعل DHCP Snooping عام على السويتش (global)**  
    ليه: لازم تفعّل الخدمة علشان السويتش يتعلم ويدير الـbinding table اللي DAI هيعتمد عليه.  
    أمر (global config):
    
    ```
    Switch(config)# ip dhcp snooping
    ```
    
    ثم فعّلها على الـVLANs المطلوبة (مثال VLAN 10):
    
    ```
    Switch(config)# ip dhcp snooping vlan 10
    ```
    
    بعد التفعيل، السويتش يبدأ يبني binding entries لكل جهاز بياخد IP عبر DHCP. ([Cisco](https://www.cisco.com/c/en/us/td/docs/switches/lan/csbss/CBS220/CLI-Guide/b_220CLI/ip_dhcp_snooping_commands.pdf?utm_source=chatgpt.com "IP DHCP Snooping Commands"))
    

