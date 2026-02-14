### 6. **تغيير تخصيص VLAN لمنفذ**
- لو عايز تغير الـ VLAN لمنفذ:
  - أعد إدخال الأمر:
    ```
    Switch(config-if)# switchport access vlan 30
    ```
  - لو عايز ترجّع المنفذ لـ VLAN 1 (الافتراضي):
    ```
    Switch(config-if)# no switchport access vlan
    ```
- تحقق من التغيير باستخدام:
  ```
  show vlan brief
  ```
  أو
  ```
  show interfaces fa0/18 switchport
  ```



![[Pasted image 20250908211512.png]]

##### الشرح للجزء  : من الدقيقه ال 1:41:58 الي الدقيقه 1:43:5
