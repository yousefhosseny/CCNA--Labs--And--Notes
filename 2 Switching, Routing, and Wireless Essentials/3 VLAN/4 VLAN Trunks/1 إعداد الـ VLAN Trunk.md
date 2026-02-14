
### 1. **إعداد الـ VLAN Trunk**
- الترنك يعمل على الـ Layer 2 ويسمح بنقل بيانات كل الـ VLANs الموجودة، إلا لو حددت VLANs معينة.
- الأوامر لإعداد الترنك:
  1. ادخل وضع الـ Global Configuration:
     ```
     Switch# configure terminal
     ```
  2. اختار المنفذ (مثل fa0/1):
     ```
     Switch(config)# interface fa0/1
     ```
  3. حدد المنفذ كـ Trunk:
     ```
     Switch(config-if)# switchport mode trunk
     ```
  4. (اختياري) غيّر الـ Native VLAN (اللي بيحمل بيانات بدون توسيم) من VLAN 1 لـ VLAN تاني (مثل 99):
     ```
     Switch(config-if)# switchport trunk native vlan 99
     ```
  5. (اختياري) حدد قايمة الـ VLANs المسموح بيها على الترنك:
     ```
     Switch(config-if)# switchport trunk allowed vlan 10,20,30,99
     ```
  6. ارجع لوضع الـ Privileged EXEC:
     ```
     Switch(config-if)# end
     ```

- **مثال عملي**:
  لو عندك شبكة فيها VLANs بالشكل ده:
  - VLAN 10 (Faculty/Staff): 172.17.10.0/24
  - VLAN 20 (Students): 172.17.20.0/24
  - VLAN 30 (Guests): 172.17.30.0/24
  - VLAN 99 (Native): 172.17.99.0/24

  عشان تعمل ترنك على منفذ fa0/1 في سويتش S1:
  ```
  S1# configure terminal
  S1(config)# interface fa0/1
  S1(config-if)# switchport mode trunk
  S1(config-if)# switchport trunk native vlan 99
  S1(config-if)# switchport trunk allowed vlan 10,20,30,99
  S1(config-if)# end
  ```
  - **ملاحظة**: المثال ده لسويتش 2960 بيستخدم معيار **802.1Q** للتوسيم. لو كنت بتستخدم سويتش Layer 3، لازم تحدد التوسيم (encapsulation) قبل وضع الترنك.

![[Pasted image 20250908211559.png]]

##### الشرح للجزء  : من الدقيقه ال 1:43:54 الي الدقيقه 00:00:00

