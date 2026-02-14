
1. **العملاء مش بياخدوا IP**
    
    - هل الواجهة عليها `ip address`؟ هل السويتش بين الراوتر والعميل يسمح DHCP (no DHCP snooping block)؟
        
    - لو السيرفر بعيد: تأكد من وجود `ip helper-address` على الـ interface الصحيح. ([Cisco](https://www.cisco.com/c/en/us/td/docs/routers/ios/config/17-x/ip-addressing/b-ip-addressing/m_iap-bph-0.html?utm_source=chatgpt.com "IP Addressing Configuration Guide, Cisco IOS XE 17.x"))
        
2. **Pool راح (exhausted)**
    
    - راجع `show ip dhcp pool` و `show ip dhcp binding`؛ شوف لو فيه عناوين محجوزة أو في conflict table. زود نطاق الشبكة أو اقلّل excluded addresses لو مناسب. ([Cisco](https://www.cisco.com/c/en/us/support/docs/routers/sd-wan/221087-configure-and-troubleshoot-a-dhcp-server.html?utm_source=chatgpt.com "Configure and Troubleshoot a DHCP Server on Cisco IOS ..."))
        
3. **Conflict/Decline**
    
    - السيرفر يعمل ping/ARP قبل يسلم IP؛ لو يكتشف رد يحط العنوان في conflict table. شوف `show ip dhcp conflict` و`clear ip dhcp conflict *` بعد حل السبب. ([firewall.cx](https://www.firewall.cx/cisco/cisco-switches/cisco-switch-router-dhcp-server-conflicts.html?utm_source=chatgpt.com "Resolving Cisco Switch & Router 'DHCP Server Pool ..."))
        
4. **الحجز الثابت مش بيشتغل**
    
    - قد يكون العميل يرسل `client-identifier` مش الـ MAC. استخدم `debug ip dhcp server packet` أو شوف `show ip dhcp binding` لتعرف الـ client-id المستخدم، وبعدين اضبط الـ pool باستخدام نفس الـ client-identifier أو `hardware-address`. ([Cisco](https://www.cisco.com/c/en/us/td/docs/ios/12_2sb/12_2sba/feature/guide/sbhcpsm.html?utm_source=chatgpt.com "DHCP - Static Mapping"))
        
5. **الـ Gateway غلط أو الـ DNS مش وصل**
    
    - تأكد الإعدادات في الـ pool (`default-router` و `dns-server`) ومطابقتها للاحتياج.
        

---
