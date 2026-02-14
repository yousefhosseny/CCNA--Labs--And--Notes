
### 3. **مثال على تشخيص وإصلاح مشكلة EtherChannel**
- **السيناريو**: منافذ F0/1 وF0/2 بين سويتشين (S1 وS2) معمول إعدادها كـ EtherChannel، بس الـ Channel مش شغال.
![[Pasted image 20250908214053.png]]

#### **الخطوة 1: التحقق من ملخص EtherChannel**
- استخدم الأمر:
  ```
  show etherchannel summary
  ```
- لو النتيجة بتقول إن الـ Port Channel "Down"، يبقى فيه مشكلة.

#### **الخطوة 2: فحص إعدادات Port Channel**
- استخدم الأمر:
  ```
  show run | begin interface port-channel
  ```
- لو لقيت إن S1 معمول إعداده بـ PAgP Auto وS2 بـ Auto، دي مشكلة لأن Auto مع Auto ما بيبدأش التفاوض، فالـ Channel مش هيتكون.

#### **الخطوة 3: إصلاح المشكلة**
- غيّر وضع PAgP على أحد الطرفين لـ **Desirable** عشان يبدأ التفاوض:
  ```
  S1# configure terminal
  S1(config)# no interface port-channel 1
  S1(config)# interface range fa0/1 - 2
  S1(config-if-range)# channel-group 1 mode desirable
  S1(config-if-range)# end
  ```
- **ملاحظة**: لازم تمسح واجهة الـ Port Channel الأول وبعدين تعيدها مع إعداد جديد، عشان تتجنب أخطاء STP (مثل المنافذ تدخل في حالة Blocking أو Errdisabled).

#### **الخطوة 4: التحقق من إن EtherChannel شغال**
- استخدم الأمر:
  ```
  show etherchannel summary
  ```
- لو الـ Port Channel ظهر "Up"، يبقى الإعداد شغال صح.

---

### **ملاحظة عن STP وEtherChannel**
- EtherChannel وSTP لازم يشتغلوا مع بعض. لو غيّرت إعدادات منفذ فيزيائي من غير ما تمسح الـ Port Channel، ممكن STP يحجب المنافذ أو يدخلها في حالة خطأ (Errdisabled).

---

