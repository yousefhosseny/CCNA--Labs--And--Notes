### 3. **تخصيص VLAN لمنفذ (Port Assignment)**
- بعد إنشاء الـ VLAN، نقدر نربطه بمنفذ معين في السويتش.
- الخطوات:
  1. ادخل وضع الـ Global Configuration:
     ```
     Switch# configure terminal
     ```
  2. اختار المنفذ (مثل fa0/18):
     ```
     Switch(config)# interface fa0/18
     ```
  3. حدد المنفذ كـ Access Port:
     ```
     Switch(config-if)# switchport mode access
     ```
  4. ربط المنفذ بالـ VLAN:
     ```
     Switch(config-if)# switchport access vlan 20
     ```
  5. ارجع لوضع الـ Privileged EXEC:
     ```
     Switch(config-if)# end
     ```

- **مثال**:
  لو عايزين نربط منفذ fa0/18 بـ VLAN 20:
  ```
  S1# configure terminal
  S1(config)# interface fa0/18
  S1(config-if)# switchport mode access
  S1(config-if)# switchport access vlan 20
  S1(config-if)# end
  ```
- بعد كده، الجهاز المتصل بالمنفذ (زي كمبيوتر طالب) هياخد عنوان IP للـ VLAN ده (مثل 172.17.20.22).


![[Pasted image 20250908211340.png]]

##### الشرح للجزء  : من الدقيقه ال 1:34:55 الي الدقيقه 00:00:00