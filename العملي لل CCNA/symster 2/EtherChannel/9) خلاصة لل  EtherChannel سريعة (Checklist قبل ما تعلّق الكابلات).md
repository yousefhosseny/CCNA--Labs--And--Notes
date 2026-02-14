1. تأكد السرعة/duplex متطابقين.
    
2. تأكد access vs trunk متطابق.
    
3. تأكد allowed VLANs و native VLAN متطابقة.
    
4. طبّق `channel-group` على الواجهات، وبعدها ظبط الـ `interface port-channel` بالإعدادات L2 المطلوبة.
    
5. تحقق بـ `show etherchannel summary` و `show interfaces port-channel 1`.
    
