3. **فعل DAI على VLANs محددة**  
    ليه: DAI مفعل بالـVLAN — لازم تحدد أي VLANs تتطبق عليها فحص ARP.  
    أمر:
    
    ```
    Switch(config)# ip arp inspection vlan 10
    ```
    
    بعد التفعيل، كل ARP packet على VLAN 10 هيتم فحصه مقابل جدول binding أو مقابل ARP ACLs لو معمولة. ([Cisco](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9300/software/release/17-9/configuration_guide/sec/b_179_sec_9300_cg/configuring_dynamic_arp_inspection.html?utm_source=chatgpt.com "Configuring Dynamic ARP Inspection [Cisco Catalyst 9300 ..."))
    
