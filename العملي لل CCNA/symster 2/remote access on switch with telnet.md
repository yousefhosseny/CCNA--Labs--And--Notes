### فديو بيشرحها 
https://youtu.be/77lpKvg99tI?si=Pemt6ZYOBdYtxs-M

### **5. إعداد المحول للإدارة عن بُعد (Switch Management Access):**

الغرض:  
إنك تقدر تدخل على السويتش عن طريق **SSH أو Telnet** من جهاز على الشبكة بدل ما تفضل معتمد على كابل الـ Console.

---

#### **الخطوات العملية:**

1. **تحديد واجهة إدارية (SVI):**
    
    - الافتراضي بيكون **VLAN 1**، لكن لأسباب أمنية يفضل نستخدم VLAN مخصصة (زي VLAN 99).
        
    - ندخل الأوامر:
        
        ```bash
        S1# configure terminal
        S1(config)# interface vlan 99
        S1(config-if)# ip address 172.17.99.11 255.255.255.0
        S1(config-if)# no shutdown
        S1(config-if)# end
        ```
        
2. **إعداد البوابة الافتراضية (Default Gateway):**
    
    - علشان السويتش يقدر يتواصل مع الأجهزة اللي برا شبكته المباشرة:
        
        ```bash
        S1# configure terminal
        S1(config)# ip default-gateway 172.17.99.1
        S1(config)# end
        ```
        
3. **حفظ الإعدادات:**
    
    - علشان الإعدادات تفضل موجودة بعد إعادة التشغيل:
        
        ```bash
        S1# copy running-config startup-config
        ```
        
4. **التحقق من الإعدادات:**
    
    - لمراجعة حالة الواجهات وعنوان الـ IP:
        
        ```bash
        show ip interface brief
        show ipv6 interface brief
        ```
        
    - هتشوف لو الواجهة Up وعليها IP مظبوط.
        

---

#### **ملاحظات مهمة:**

- العنوان اللي بتحطه على واجهة الـ SVI ده **مخصص للإدارة فقط** (Management)، مش بيخلي السويتش يشتغل كـ Router.
    
- لو هتحتاج إدارة عن طريق **IPv6**:
    
    - فعل دعم الـ IPv6 مع الـ IPv4:
        
        ```bash
        sdm prefer dual-ipv4-and-ipv6 default
        ```
        
    - وبعدها لازم تعمل **reload** للسويتش.
        

---

تحب أعملك كمان شرح للجزء اللي بعد كده (زي إعداد الـ **SSH Access** بدل الـ Telnet) علشان تكمل إعداد الإدارة عن بُعد بأمان؟