### 7. **حذف VLAN**
- لحذف VLAN معين:
  ```
  Switch(config)# no vlan 20
  ```
  **ملاحظة**: لازم ترجّع أي منافذ مرتبطة بالـ VLAN ده لـ VLAN تاني قبل الحذف.
- لحذف كل الـ VLANs:
  ```
  Switch# delete flash:vlan.dat
  ```
  وبعد كده اعمل ريستارت للسويتش (reload).
- لإرجاع السويتش للإعدادات الافتراضية:
  1. افصل كل كابلات البيانات.
  2. امسح الـ startup-config:
     ```
     Switch# erase startup-config
     ```
  3. امسح ملف vlan.dat:
     ```
     Switch# delete flash:vlan.dat
     ```
  4. اعمل ريستارت:
     ```
     Switch# reload
     ```

##### الشرح للجزء  : من الدقيقه ال 1:43:5 الي الدقيقه 1:43:49

