
#### 2. **التحقق من إعدادات الواجهات (Verify Interface Configuration):**
بعد تهيئة الواجهات، لازم تتأكد إنها شغالة صح باستخدام أوامر التحقق:

- **أوامر التحقق الرئيسية:**
  1. **show ip interface brief:**
     - بيوريك حالة كل الواجهات (IP، الحالة، البروتوكول).
     - مثال:
       ```
       R1# show ip interface brief
       Interface              IP-Address      OK?  Method  Status                Protocol
       GigabitEthernet0/0/0   192.168.10.1    YES  manual  up                    up
       GigabitEthernet0/0/1   209.165.200.225 YES  manual  up                    up
       Vlan1                  unassigned      YES  unset   administratively down down
       ```
     - **Status: up** يعني الواجهة مفعلة، **Protocol: up** يعني البروتوكول شغال.
![[Pasted image 20250718232719.png]]

  2. **show ipv6 interface brief:**
     - زي السابق، بس لعناوين IPv6.
     - مثال:
       ```
       R1# show ipv6 interface brief
       GigabitEthernet0/0/0   [up/up]
           FE80::201:C9FF:FE89:4501
           2001:DB8:ACAD:10::1
       GigabitEthernet0/0/1   [up/up]
           FE80::201:C9FF:FE89:4502
           2001:DB8:FEED:224::1
       Vlan1                  [administratively down/down]
       ```

![[Pasted image 20250718232742.png]]

  2. **show ip route:**
     - بيوريك جدول التوجيه (Routing Table) لـ IPv4، يعني الشبكات اللي الروتر متصل بيها.
     - مثال:
       ```
       C 192.168.10.0/24 is directly connected, GigabitEthernet0/0/0
       C 209.165.200.224/30 is directly connected, GigabitEthernet0/0/1
       ```
       (`C` يعني الشبكة متصلة مباشرة).
  
![[Pasted image 20250718232615.png]]

  3. **show ipv6 route:**
     - زي السابق، بس لـ IPv6.
     - مثال:
       ```
       C 2001:DB8:ACAD:10::/64 via GigabitEthernet0/0/0, directly connected
       C 2001:DB8:FEED:224::/64 via GigabitEthernet0/0/1, directly connected
       ```

![[Pasted image 20250718232654.png]]

  4. **show interfaces:**
     - بيوريك إحصائيات مفصلة عن الواجهات (زي الحالة، السرعة، عدد الحزم).
     - مثال:
       ```
       R1# show interfaces gigabitEthernet0/0/0
       GigabitEthernet0/0/0 is up, line protocol is up
       Description: Link to LAN
       Internet address is 192.168.10.1/24
       ```
  5. **show ip interface:**
     - بيوريك إحصائيات IPv4 للواجهات (مثل العنوان، إعدادات الأمان).
![[Pasted image 20250718232836.png]]

  6. **show ipv6 interface:**
     - بيوريك إحصائيات IPv6 للواجهات.

![[Pasted image 20250718232850.png]]


---


