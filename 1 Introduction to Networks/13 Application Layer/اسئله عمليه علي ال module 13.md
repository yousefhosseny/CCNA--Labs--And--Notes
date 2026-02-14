
## ✅ قائمة الأسئلة العملية على Packet Tracer:

### 1- HTTP / HTTPS

- أضف **Server** في Packet Tracer، وفعل عليه **HTTP Service**.
    
- خليه يستضيف صفحة ويب (index.html).
    
- وصل PC بالـ Server وجرب الدخول على الموقع بكتابة عنوان الـ Server في المتصفح.
    
- جرّب طلب صفحة بـ **GET Request** (هيحصل تلقائي لما تكتب العنوان في المتصفح).
    

---

### 2- Email Protocols (SMTP, POP, IMAP)

- على نفس الـ Server فعل خدمة **Email (SMTP + POP + IMAP)**.
    
- أنشئ حسابين بريد إلكتروني على السيرفر.
    
- من جهازين مختلفين (PC1 و PC2)، جرب:
    
    - إرسال إيميل من PC1 إلى PC2 (SMTP).
        
    - استلام الإيميل على PC2 (POP/IMAP).
        

---

### 3- DNS Service

- أنشئ **DNS Server**.
    
- ضيف له record باسم: `www.test.com` يترجم لـ IP السيرفر بتاع الويب.
    
- على جهاز Client، بدل ما تدخل IP السيرفر في المتصفح، اكتب `www.test.com` وشوف هل هيترجم الاسم لـ IP صح.
    
- جرّب كمان الأمر `nslookup www.test.com` من الـ Command Prompt.
    

---

### 4- DHCP Service

- فعل خدمة **DHCP** على السيرفر.
    
- اعمل Pool يوزع IPs مثلاً من: `192.168.1.10 – 192.168.1.50`.
    
- خلّي 3 أجهزة Clients ياخدوا IPs أوتوماتيك من DHCP.
    
- اعمل اختبار بالـ `ipconfig /renew` من الـ Command Prompt وشوف الـ Lease.
    

---

### 5- FTP Service

- فعّل خدمة **FTP** على السيرفر.
    
- من جهاز Client جرب الدخول على السيرفر باستخدام FTP client في Packet Tracer.
    
- جرّب تحميل (Download) ملف من السيرفر ورفع (Upload) ملف للسيرفر.
    

---

### 6- SMB (File & Printer Sharing)

- فعل خدمة **SMB** على السيرفر.
    
- اربط جهازين بالسيرفر.
    
- من جهاز Client، ادخل على الملفات أو الطابعة اللي شاركها السيرفر.
    
- لاحظ الفرق إن الاتصال بيبقى **long-term connection** مش زي FTP اللي بيعمل اتصالين منفصلين.
    

---
