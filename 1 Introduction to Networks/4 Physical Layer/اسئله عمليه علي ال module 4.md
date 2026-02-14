
### **1. اختبار أنواع الكابلات (UTP, STP, Coaxial)**

- جرب توصيل **2 PCs** باستخدام:
    
    - كابل **Straight-through** (2 PC → Switch).
	    -  PC0: IP = `192.168.1.2` ، Subnet = `255.255.255.0`
    
		- PC1: IP = `192.168.1.3` ، Subnet = `255.255.255.0`
        
    - كابل **Crossover** (PC ↔ PC مباشرة).	    
	    - PC0: IP = `192.168.1.2` ، Subnet = `255.255.255.0`
    
		- PC1: IP = `192.168.1.3` ، Subnet = `255.255.255.0`
    
        
    - كابل **Rollover** (PC Console → Router).
        
- شغّل **ping** بينهم وشوف هل الاتصال شغال ولا لأ.  
    (جرب كمان لو بدلت الأطراف هل يحصل مشكلة ولا Auto-MDIX يحلها).

#### شرح اللاب :

####  حل اللاب :


#### خطوات حل اللاب :
![[Whiteboard 30.png]]

---


### 2. تجربة الـ NIC (Network Interface Card)
![[تجربة الـ NIC (Network Interface Card).pkt]]**

- افتح خصائص أي PC في Packet Tracer وشوف:
    
    - هل عنده **Wired NIC** فقط ولا تقدر تضيف **Wireless NIC**؟
        
    - جرّب تعمل **Disable NIC** وشوف إنه مش هيتصل.

#### شرح اللاب :


####  حل اللاب :

![[تجربة الـ NIC (Network Interface Card).pkt]]

#### خطوات حل اللاب :
![[Whiteboard 31.png]]

---

### 3. التوصيل بالـ Cloud

- في Packet Tracer فيه جهاز اسمه **Cloud**:
    
    - اربط Router بـ Cloud (مثلاً عبر Serial أو DSL).
        
    - وصل 2 شبكات صغيرة بالـ Router.
        
    - جرب Ping بين شبكتين مختلفتين عشان تفهم إزاي الـ Cloud بيشتغل كـ WAN.
        

---
اللاب اهو

![[4.7.2 Packet Tracer - Connect the Physical Layer.pka]]

حل اللاب اهو

###### شرح حل اللاب 

----
اللاب اهو

![[4.6.5 Packet Tracer - Connect a Wired and Wireless LAN.pka]]

حل اللاب اهو

###### شرح حل اللاب 

----

اللاب اهو

![[4.7.1 Packet Tracer - Connect the Physical Layer.pka]]
حل اللاب اهو

###### شرح حل اللاب 

----

