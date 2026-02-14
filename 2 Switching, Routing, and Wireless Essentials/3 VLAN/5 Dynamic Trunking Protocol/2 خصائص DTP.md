
### 2. **خصائص DTP**
- **مفعّل افتراضيًا** على سويتشات Cisco Catalyst زي 2960 و2950.
- الوضع الافتراضي هو **Dynamic Auto** على السويتشات دي.
- ممكن **تعطّله** بأمر:
  ```
  switchport nonegotiate
  ```
- لو عايز ترجّعه للوضع التلقائي، استخدم:
  ```
  switchport mode dynamic auto
  ```
- لو عايز تتجنب مشاكل التفاوض، اعمل المنفذ **ترنك ثابت** أو **أكسس ثابت** بأوامر:
  ```
  switchport mode trunk
  ```
  أو
  ```
  switchport mode access
  ```
