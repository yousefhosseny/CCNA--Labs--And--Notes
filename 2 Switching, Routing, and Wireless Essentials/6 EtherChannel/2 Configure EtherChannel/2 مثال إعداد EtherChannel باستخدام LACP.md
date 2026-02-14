
###  **مثال إعداد EtherChannel باستخدام LACP**
لإعداد EtherChannel باستخدام **LACP** (بروتوكول IEEE 802.3ad)، اتبع الخطوات دي على سويتش (مثل S1):
1. **حدد المنافذ اللي هتكون جزء من الـ EtherChannel**:
   - استخدم أمر `interface range` عشان تختار كذا منفذ مع بعض:
     ```
     S1# configure terminal
     S1(config)# interface range fa0/1 - 2
     ```
     (هنا بنختار المنفذين FastEthernet 0/1 و0/2).

2. **إنشاء واجهة Port Channel**:
   - استخدم أمر `channel-group` مع وضع **Active** لتفعيل LACP:
     ```
     S1(config-if-range)# channel-group 1 mode active
     S1(config-if-range)# end
     ```
     - `1` هو رقم الـ Channel Group (ينفع تختار أي رقم).
     - `mode active` بيخلي المنافذ تبدأ التفاوض بنشاط مع الجهاز التاني.

3. **إعداد واجهة الـ Port Channel** (اختياري):
   - لو عايز تغيّر إعدادات Layer 2 (زي جعل الـ Port Channel ترنك):
     ```
     S1(config)# interface port-channel 1
     S1(config-if)# switchport mode trunk
     S1(config-if)# switchport trunk allowed vlan 10,20,99
     S1(config-if)# end
     ```
     - هنا بنعمل الـ Port Channel ترنك ونحدد الـ VLANs المسموح بيها (مثل 10، 20، 99).

---
