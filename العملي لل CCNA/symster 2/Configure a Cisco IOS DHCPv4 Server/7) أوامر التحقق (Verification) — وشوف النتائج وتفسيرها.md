
- `show running-config | section dhcp`  
    يظهر تعريفات الـ pools وexcluded-addresses. ([Cisco](https://www.cisco.com/c/en/us/support/docs/routers/sd-wan/221087-configure-and-troubleshoot-a-dhcp-server.html?utm_source=chatgpt.com "Configure and Troubleshoot a DHCP Server on Cisco IOS ..."))
    
- `show ip dhcp pool`  
    يعرض إحصاءات كل Pool: عدد العناوين المسموح بها، عدد المستخدم/الفارغ، utilization.
    
- `show ip dhcp binding`  
    يعرض العناوين الممنوحة حالياً مع client-id/ MAC ووقت انتهاء الـ lease. مهم جداً لمعرفة من أخذ عنوان. ([Cisco](https://www.cisco.com/c/en/us/support/docs/routers/sd-wan/221087-configure-and-troubleshoot-a-dhcp-server.html?utm_source=chatgpt.com "Configure and Troubleshoot a DHCP Server on Cisco IOS ..."))
    
- `show ip dhcp server statistics`  
    يعرض إحصاءات الرسائل (DHCPOFFER, DHCPACK, DHCPNACK...) وعدد العناوين المخصصة/المنتهية.
    
- `show ip dhcp conflict`  
    لو فيه عناوين في conflict table (تم اكتشافها عن طريق ARP/ ping) يبقى لازم تشيلهم أو تحل سبب التعارض.
    
- Debug مفيد: `debug ip dhcp server packet` أو `debug ip dhcp server events` (استعمله في نافذة صيانة لأن الـ debug يهيج الـ CPU).
    

---
