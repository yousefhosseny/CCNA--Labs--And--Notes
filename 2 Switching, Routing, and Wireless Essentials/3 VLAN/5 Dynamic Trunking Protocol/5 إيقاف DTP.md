### 5. **إيقاف DTP**
- لو عايز تتجنب التفاوض التلقائي عشان تتحكم يدويًا في المنفذ:
  ```
  Switch(config)# interface fa0/1
  Switch(config-if)# switchport mode trunk
  Switch(config-if)# switchport nonegotiate
  Switch(config-if)# end
  ```
- الأمر `switchport nonegotiate` بيوقف DTP، يعني المنفذ هيفضل زي ما أنت محدده (ترنك أو أكسس) من غير ما يتفاوض مع السويتش التاني.

