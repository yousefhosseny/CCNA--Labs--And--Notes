### على S1 (الطرف A)

```
S1# configure terminal
S1(config)# interface range fa0/1 - 2
S1(config-if-range)# channel-group 1 mode active
S1(config-if-range)# end
```

- `interface range fa0/1 - 2` : بنحدد المنافذ اللي هنجمّعها. (ممكن تستخدم Gi/Te حسب البورت).
    
- `channel-group 1` : رقم مجموعة الـ Channel — هو نفس الرقم على الطرف التاني بس مش لازم يكون متطابق بالضرورة على سيسكات غير متشابهة، لكن أفضل تطابقه.
    
- `mode active` : هذا يفعل LACP بشكل نشط — السويتش هيبعت LACP PDUs للتفاوض.
    

بعدها نضبط الواجهة المنطقية (Port-Channel):

```
S1(config)# interface port-channel 1
S1(config-if)# switchport mode trunk
S1(config-if)# switchport trunk allowed vlan 10,20,99
S1(config-if)# end
```

- كل إعداد Layer-2 (trunk/access, allowed VLANs, native VLAN, mtu، إلخ) يُطبَّق على `port-channel` وليس على الواجهات الفردية (أو على الأقل يجب أن تكون متطابقة).
    

### على S2 (الطرف B) — مثال passive

```
S2# configure terminal
S2(config)# interface range fa0/1 - 2
S2(config-if-range)# channel-group 1 mode passive
S2(config-if-range)# end

S2(config)# interface port-channel 1
S2(config-if)# switchport mode trunk
S2(config-if)# switchport trunk allowed vlan 10,20,99
S2(config-if)# end
```

- `mode passive` : يستقبل LACP لكن لا يرسل PDUs بشكل نشط؛ لحد ما الطرف التاني يكون `active` أو `passive` مع `active` على الناحية المقابلة.
    
