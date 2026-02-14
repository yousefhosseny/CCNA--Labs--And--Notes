
## 🔹 السيناريو

- عندك سويتشين (S1 و S2) متوصلين بكابلات على المنافذ `fa0/1` و `fa0/2`.
    
- عايزين نعمل **EtherChannel باستخدام LACP**.
    
- نخلي الواجهة الجديدة (Port-Channel 1) شغالة كـ **Trunk** وتسمح بالـ VLANs: `10,20,99`.
    

---

## 🔹 الإعداد على **S1**

```
S1> enable
S1# configure terminal
S1(config)# interface range fa0/1 - 2
S1(config-if-range)# channel-group 1 mode active
S1(config-if-range)# exit
S1(config)# interface port-channel 1
S1(config-if)# switchport mode trunk
S1(config-if)# switchport trunk allowed vlan 10,20,99
S1(config-if)# end
S1# write memory
```

---

## 🔹 الإعداد على **S2**

```
S2> enable
S2# configure terminal
S2(config)# interface range fa0/1 - 2
S2(config-if-range)# channel-group 1 mode passive
S2(config-if-range)# exit
S2(config)# interface port-channel 1
S2(config-if)# switchport mode trunk
S2(config-if)# switchport trunk allowed vlan 10,20,99
S2(config-if)# end
S2# write memory
```

---

## 🔹 أوامر التحقق

بعد ما تخلص الإعداد، على **الطرفين** نفّذ:

1. **ملخص EtherChannel**
    

```
S1# show etherchannel summary
```

🔹 إخراج متوقّع:

```
Group  Port-channel  Protocol    Ports
------+-------------+----------+----------------
1      Po1(SU)       LACP       Fa0/1(P) Fa0/2(P)
```

- `Po1(SU)` معناها Port-channel 1 Up & Layer2.
    
- `(P)` جنب كل منفذ يعني **Bundled in Port-Channel**.
    

---

2. **تفاصيل EtherChannel**
    

```
S1# show etherchannel detail
```

🔹 هتشوف حالة كل منفذ، وسبب أي منفذ خارج القناة (لو في mismatch).

---

3. **تشيك الـ Trunk**
    

```
S1# show interfaces port-channel 1 switchport
```

🔹 إخراج متوقّع:

```
Port-channel1 is trunking
Allowed VLANs: 10,20,99
```

---

4. **تشيك الـ Spanning-Tree**
    

```
S1# show spanning-tree interface port-channel 1
```

🔹 هتلاقي الـ Port-Channel ظاهر كمنفذ واحد في الـ STP.

---

## 🔹 Troubleshooting سريع

- لو لقيت `suspended` → فيه اختلاف في VLANs أو trunk/native config.
    
- لو لقيت منفذ `(I)` يعني **individual** مش joined → غالبًا mismatch.
    
- الحل: خلّي كل الإعدادات على `port-channel` نفسه مش على المنافذ الفردية.
    

---

