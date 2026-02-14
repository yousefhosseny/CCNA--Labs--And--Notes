4. **حدد المنافذ الموثوقة (trusted) لـDHCP Snooping وDAI**  
    ليه: المنافذ المتجهة لروتر/سويتش آخر أو لسيرفر DHCP لازم تكون **trusted** عشان لا يتم حظر رسائل DHCP أو ARP المشروعة عبر uplink أو لمنفذ سيرفر. باقي الـaccess ports لازم تكون **untrusted** بشكل افتراضي.  
    مثال: على uplink interface:
    
    ```
    Switch(config)# interface GigabitEthernet1/0/1
    Switch(config-if)# ip dhcp snooping trust
    Switch(config-if)# ip arp inspection trust
    ```
    
    وعلى access port (مستخدم عادي): لا تضيف trust — ويفضل تحدد حد لعدد طلبات DHCP على الواجهة:
    
    ```
    Switch(config)# interface GigabitEthernet1/0/10
    Switch(config-if)# switchport mode access
    Switch(config-if)# switchport access vlan 10
    Switch(config-if)# ip dhcp snooping limit rate 10
    Switch(config-if)# ip arp inspection limit rate 15
    ```
    
    المبدأ: كل access ports untrusted، uplinks & DHCP servers trusted. ([ComputerNetworkingNotes](https://www.computernetworkingnotes.com/ccna-study-guide/configure-dhcp-snooping-on-cisco-switches.html?utm_source=chatgpt.com "Configure DHCP Snooping on Cisco Switches"))
    
    

