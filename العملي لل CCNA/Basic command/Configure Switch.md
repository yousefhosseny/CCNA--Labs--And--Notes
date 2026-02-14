يعني اي Configure Switch يعني لما انا بوصل جهاز end device مع ال Switch وعايزهم يكونوا شايفين بعض  

#### 1.  اول حاجه ان بعمل vlan واحده وبديها اسم
```bash
en
conf t
vlan 10
name [اسم اللي انت عايزه]
exit
```

#### 2. بنحط الـ IP على VLAN اللي عملتها
يعني إيه؟ يعني لما تحط IP على `interface vlan 1`، فـ انت بتدي للسويتش نفسه عنوان IP عشان:

- تقدر توصل له عن طريق الشبكة (مثلاً من جهازك باستخدام telnet أو SSH).
    
- تقدر تعمل عليه إدارة عن بُعد (remote management).
    
- السويتش نفسه يعرف يرد على الـ ping من جهازك.

```bash
en
conf t
interface vlan [رقمها]
ip address [ip بتاع ال vlan] [subnet mask بتاع ال vlan]
no shutdown
exit
```

#### 3.  علشان اضيف الاجهزه لل vlan اللي عملتها دي بقا

```bash
en
conf t
interface fastEthernet [رقم بورت الجهاز] || interface range fastEthernet 0/1 - 5 
switchport mode access
switchport access vlan [رقمها]
no shutdown
exit
```


#### 4.تحديد Default Gateway 

```bash
en
conf t
 ip default-gateway 192.168.1.1
```

#### الشرح العملي :
![[2025-08-02 10-43-32.mkv]]