# 1.  تهيئة ال Interfaces ل ال Router

#### - لو ipv4
```bash
en
conf t
interface [نوع-ورقم]
 ip address [عنوان IPv4] [Subnet Mask]
  description LAN connection to S1
 no shutdown
 exit
```

  #### لو ipv6
  
```bash
en
conf t
interface [نوع-ورقم]
 ipv6 address [عنوان IPv6]/[طول القناع]
  description LAN connection to S1
  no shutdown
  exit
```
![[Pasted image 20250718232332.png|846]]



# 2. التحقق من إعدادات الواجهات

### أوامر التحقق الرئيسية:
  1. ء **show ip interface brief:**
     - بيوريك حالة كل الواجهات لل الراوتر (IP، الحالة، البروتوكول).
```
en
       show ip interface brief
```
لو **Status: up** يعني الواجهة مفعلة، **Protocol: up** يعني البروتوكول شغال.
![[Pasted image 20250718232719.png]]

  2. ء**show ipv6 interface brief:**
     - زي السابق، بس لعناوين IPv6.
```
en
       show ipv6 interface brief
```
![[Pasted image 20250718232742.png]]

3. **show ip route:**
-  بيوريك جدول التوجيه (Routing Table) لـ IPv4، يعني الشبكات اللي الروتر متصل بيها.
```
en
      show ip route
```
![[Pasted image 20250718232615.png]]

4. **show interfaces:**
     - بيوريك إحصائيات مفصلة عن الواجهات (زي الحالة، السرعة، عدد الحزم).
```
en
       show ip interface [نوع-ورقم]
```
![[Pasted image 20250718232836.png]]

#### لاب عملي علي الجزء ده 

اللاب اهو

حل اللاب اهو


# 3. Default Gateway on a Switch(لسه عايزه تتشرح )

 - بدون البوابة الافتراضية، السويتش مش هيقدر يرد على طلبات من شبكات خارجية.
```
ip default-gateway [عنوان IP]
```
  - مثال: `ip default-gateway 192.168.10.1` (عنوان واجهة الروتر).


#### لاب عملي علي الجزء ده 

اللاب اهو

حل اللاب اهو



------

