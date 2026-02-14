
1. **المنفذ مش بيلتحم (ما بيدخلش في channel)**
    
    - تحقق من mismatch في: speed, duplex, native VLAN, allowed VLANs, switchport mode.
        
    - أوامر مفيدة:
        
        - `show interfaces fa0/1`
            
        - `show interfaces fa0/1 switchport`
            
        - `show running-config interface fa0/1`
            
    - الحل: خَلِّي إعدادات الواجهة الفردية أو Port-Channel متطابقة، أو افعل الإعداد على `port-channel` وأعد ضم المنافذ.
        
2. **كل الإدخالات مبعثرة أو أحد المنافذ suspended**
    
    - السبب غالبًا اختلاف config أو وجود إعداد layer3 على واجهة واحده.
        
    - راجع الـ logs: `show logging` أو `show etherchannel detail` للحصول على تفاصيل سبب التعليق.
        
3. **الـ EtherChannel اتكوَّن لكن الترنك مش شغال أو VLANs غير متطابقة**
    
    - تأكد أن `switchport trunk allowed vlan` و `native vlan` مطابقة على الطرفين وفي `port-channel` نفسه.
        
4. **لو لقيت أن TCP flow مش بيستخدم aggregate bandwidth**
    
    - دي خاصية معروفة: hashing يوزع التدفقات، وتدفق واحد غالبًا محصور على رابط واحد. مافيش حاجة غلط؛ لو عايز ترفع throughput لتدفق واحد لازم تستخدم حلول أخرى (مثل Session-based balancing من التطبيقات أو تغيير طريقة الhash لو الجهاز بيدعم).
        
