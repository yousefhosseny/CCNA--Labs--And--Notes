## الوصف :
ده Static Routes العادي اللي هو انا عايز اوصل الراوتر بشبكه معينه بطريقه ال Static  

## الخطوات 
- الأمر:
  ```bash
  ip route network-address subnet-mask  ip-address   exit-intf     [distance]
  ```
- **التفسير**:
  - ال`network-address`: عنوان الشبكة اللي عايز الراوتر يشوفها  (مثل 192.168.1.0).
  - ال`subnet-mask`: قناع الشبكة   اللي عايز الراوتر يشوفها (مثل 255.255.255.0).
  - ال`ip-address`: عنوان IP للراوتر التالي (Next-Hop).
  - ال`exit-intf`:  ال interface اللي هيخرج منه
  - ال`distance`: الـ Administrative Distance (اختياري، القيمة الافتراضية 1).

## ملحوظه : 

عايزك تحط الاثنين دولي  ip-address و   exit-intf   مع بعض مش تعمل واحده وتانيه لا علشان تتجنب اي مشكله 

---

