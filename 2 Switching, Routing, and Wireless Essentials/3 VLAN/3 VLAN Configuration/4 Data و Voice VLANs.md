
### 4. **Data و Voice VLANs**
- كل منفذ (Access Port) ينفع يتربط بـ **VLAN واحد للداتا** فقط.
- لكن لو في هاتف VoIP متصل بنفس المنفذ مع كمبيوتر، ينفع نضيف **Voice VLAN** إضافي.
- بيانات الصوت بتاخد أولوية (QoS) عشان جودة المكالمات.
- لو ربطنا Voice VLAN لمنفذ، السويتش هينشئ الـ VLAN تلقائيًا لو مش موجود.

- **مثال لإعداد Data و Voice VLAN**:
  1. إنشاء VLAN للداتا (مثل VLAN 20) وVLAN للصوت (مثل VLAN 100).
  2. ربط المنفذ بـ VLAN الداتا وVLAN الصوت مع تفعيل QoS:
     ```
     Switch# configure terminal
     Switch(config)# vlan 20
     Switch(config-vlan)# name student
     Switch(config)# vlan 100
     Switch(config-vlan)# name voice
     Switch(config)# interface fa0/18
     Switch(config-if)# switchport mode access
     Switch(config-if)# switchport access vlan 20
     Switch(config-if)# switchport voice vlan 100
     Switch(config-if)# mls qos trust cos
     Switch(config-if)# end
     ```



![[Pasted image 20250908211356.png]]



##### الشرح للجزء  : من الدقيقه ال 1:38:32 الي الدقيقه 1:41:41