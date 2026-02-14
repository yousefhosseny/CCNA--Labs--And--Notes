1. **السرعة والـ duplex**: كل المنافذ لازم تكون نفس السرعة و نفس الـ duplex.  
    `show interfaces fa0/1` / `show interfaces gi0/1` للتأكد.
    
2. **نوع المنفذ (access vs trunk)**: كل المنفذ لازم يكون نفس النوع (لو access كلهم على VLAN واحد؛ لو trunk كلهم trunk ونفس allowed VLANs).  
    `show interfaces fa0/1 switchport`
    
3. **Native VLAN (لو trunk)**: لازم تكون متطابقة على كل المنافذ.
    
4. **VLANs المسموح بيها على ال trunk**: لازم تكون متطابقة (مثال: `10,20,99`).
    
5. **لا تنفّذ إعدادات Layer2 (مثل trunk/native/allowed) على المنافذ الفعلية بعد إضافة channel** — خليها على `interface port-channel` عشان المتعضدين يرثوا الإعدادات بشكل صحيح.
    
