
# 1. **Network Components**
 ## 📝 **سؤال عملي:** 
- اعمل شبكة صغيرة فيها:   
	  - سيرفر (Web Server).
	- عميل (PC) يتصل بالسيرفر ويطلب صفحة ويب.    
	 - اربطهم بسويتش.
	 - ال IP لل pc =192.168.10.20 
	 - ال IP لل 192.168.10.10= server
		
####  حل اللاب :

![[Network Components 1.pkt]]

#### خطوات حل اللاب :
![[Whiteboard 25.png]]

---

# 2. **Network Representations and Topologies**

## - 📝 **سؤال عملي:**
- ارسم على Packet Tracer:

- ء Physical topology لشبكة فيها  2PCs + Switch + Router.
 
- ء Logical topology موضح فيه الـIP Address لكل جهاز.
-   ال IP لل pc1 =192.168.10.11  و  ال IP لل pc2 =192.168.10.12 
- ال Default Gateway = 192.168.10.1/24

#### حل اللاب :

![[Network Representations and Topologies.pkt]]
#### شرح اللاب :
اوامر اعداد الراوتر 
```bash
enable
configure terminal
hostname R1
configure terminal
interface g0/0/0
 ip address 192.168.10.1 255.255.255.0
 no shutdown
 description To-SW1 Fa0/24
exit
do show ip interface brief

```

جنب كل جهاز اكتب:

- **PC1**
    
    - NIC: Fa0
        
    - IP: `192.168.10.11/24`
        
    - GW: `192.168.10.1`
        
- **PC2**
    
    - NIC: Fa0
        
    - IP: `192.168.10.12/24`
        
    - GW: `192.168.10.1`
        
- **R1**
    
    - G0/0: `192.168.10.1/24`
        
- **SW1**
    
    - Fa0/1 ← PC1
        
    - Fa0/2 ← PC2
        
    - Fa0/24 ← R1


#### خطوات حل اللاب :
![[Whiteboard 26.png]]

---



