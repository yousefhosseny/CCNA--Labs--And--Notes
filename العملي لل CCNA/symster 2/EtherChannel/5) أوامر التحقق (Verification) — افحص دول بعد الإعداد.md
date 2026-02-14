
- `show etherchannel summary` — نظرة سريعة هل الـ Port-Channel شغال ونه؟ مين الأعضاء bundled؟
    
- `show interfaces port-channel 1` — حالة الـ Port-Channel (up, protocol LACP, trunk info).
    
- `show running-config interface port-channel 1` — تشيك الإعدادات المطبقة.
    
- `show interfaces fa0/1 switchport` — تتأكد إن المنفذ member الحالة بتاعته.
    
- `show spanning-tree interface port-channel 1` — حالة STP للـ Port-Channel.
    

**ماذا تتوقّع أن تري؟**

- الواجهات الأعضاء تظهر على انها **bundled** داخل الـ Port-Channel، والـ Port-Channel نفسه في حالة up/up (Layer2) أو up/up (Layer3) حسب الإعداد.
    

> ملاحظة: إخراج الـ IOS قد يختلف شكل العلامات لكن الفكرة: الأعضاء يجب أن تكون مشمولة (bundled) والـ Port-Channel جاهز.
