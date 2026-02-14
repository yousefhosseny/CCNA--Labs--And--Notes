
### 2. **إنشاء VLAN**
- بيانات الـ VLAN بتتخزن في ملف **vlan.dat** في الفلاش.
- خطوات إنشاء VLAN:
  1. ادخل وضع الـ Global Configuration:
     ```
     Switch# configure terminal
     ```
  2. أنشئ VLAN برقم معين (مثل VLAN 20):
     ```
     Switch(config)# vlan 20
     ```
  3. سمّي الـ VLAN (اختياري، لو ما سميتهوش هياخد اسم افتراضي زي vlan0020):
     ```
     Switch(config-vlan)# name student
     ```
  4. ارجع لوضع الـ Privileged EXEC:
     ```
     Switch(config-vlan)# end
     ```

- **مثال**:
  لو عايزين ننشئ VLAN 20 للطلاب:
  ```
  S1# configure terminal
  S1(config)# vlan 20
  S1(config-vlan)# name student
  S1(config-vlan)# end
  ```



![[Pasted image 20250908211305.png]]

##### الشرح للجزء  : من الدقيقه ال 1:32:40 الي الدقيقه 1:34:55
