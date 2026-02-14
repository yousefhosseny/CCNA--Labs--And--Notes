
## ✅ قائمة الأسئلة العملية لموديول 7 (على Packet Tracer):

### 1- خصائص الـ Network Layer

- جرب إعداد شبكة صغيرة (PC – Switch – Router – PC) واعمل بين الأجهزة **Ping**، ولاحظ إن IP بيشتغل _connectionless_ (يعني مش بيعمل اتصال قبل الإرسال).
    
- جرّب توقف (shutdown) واجهة الراوتر، وحاول تعمل Ping ولاحظ إن مفيش ضمان توصيل (Best Effort).
    

---

### 2- Host Routing Table (Routing عند الهوست)

- افتح جهاز PC في Packet Tracer، وشوف الـ Routing Table باستخدام الأمر:
    
    ```
    netstat -r
    ```
    
    أو
    
    ```
    route print
    ```
    
- اعمل سيناريوهات:
    
    - ء Ping لنفس الجهاز (Loopback: 127.0.0.1 أو ::1 في IPv6).
        
    - ء Ping لجهاز في نفس الشبكة.
        
    - ء Ping لجهاز في شبكة تانية (يمر عن طريق Default Gateway).
        

---

### 3- Default Gateway

- جرب جهاز PC بدون ما تحط له Default Gateway، وحاول تبعته Ping لشبكة تانية → هتفشل.
    
- بعد كده ضيف Default Gateway صحيح → المفروض الاتصال ينجح.
    

---

### 4- Router Routing Tables

- اعمل شبكة مكونة من **3 Routers** متصلة ببعض وكل واحد موصل PC.
    
- جرّب الأوامر:
    
    ```
    show ip route
    ```
    
    - لاحظ الفرق بين:
        
        - C (Connected)
            
        - L (Local)
            
        - S (Static)
            
- أضف **Static Route** يدوي بين راوترين مش متصلين مباشرة، وجرب Ping.
    
- بعدين جرّب إعداد **Dynamic Routing Protocol** (مثلاً RIP v2 عشان بسيط في Packet Tracer)، وشوف ازاي الروترات بتتعلم الشبكات أوتوماتيك.
    

---


