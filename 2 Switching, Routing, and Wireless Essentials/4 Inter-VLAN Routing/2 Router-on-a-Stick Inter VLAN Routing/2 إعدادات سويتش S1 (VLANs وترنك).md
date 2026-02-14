
### 2. **إعدادات سويتش S1 (VLANs وترنك)**
عشان نقدر ننقل البيانات بين VLANs، لازم نعمل الإعدادات دي على S1:
1. **إنشاء وتسمية الـ VLANs**:
   ```
   S1# configure terminal
   S1(config)# vlan 10
   S1(config-vlan)# name FACULTY
   S1(config)# vlan 20
   S1(config-vlan)# name STUDENTS
   S1(config)# vlan 99
   S1(config-vlan)# name NATIVE
   S1(config-vlan)# end
   ```
2. **إعداد واجهة الإدارة (Management Interface)**:
   - لو عايزين نعطي S1 عنوان IP في VLAN 99 (مثلًا):
   ```
   S1(config)# interface vlan 99
   S1(config-if)# ip address 192.168.99.2 255.255.255.0
   S1(config-if)# end
   ```
3. **إعداد منافذ الأكسس (Access Ports)**:
   - لربط أجهزة زي PC1 بـ VLAN 10:
   ```
   S1(config)# interface fa0/6
   S1(config-if)# switchport mode access
   S1(config-if)# switchport access vlan 10
   S1(config-if)# end
   ```
4. **إعداد منافذ الترنك (Trunk Ports)**:
   - لربط S1 مع الراوتر (منفذ F0/5) ومع S2 (منفذ F0/1):
   ```
   S1(config)# interface fa0/5
   S1(config-if)# switchport mode trunk
   S1(config-if)# switchport trunk native vlan 99
   S1(config-if)# switchport trunk allowed vlan 10,20,99
   S1(config-if)# end
   ```

---
### الشرح للجزء  : من الدقيقه ال 02:32:50 الي الدقيقه  00:00:00