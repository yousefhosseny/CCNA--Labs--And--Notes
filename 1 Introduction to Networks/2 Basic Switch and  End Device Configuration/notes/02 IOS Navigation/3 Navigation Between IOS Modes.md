
#### 3. **التنقل بين الأوضاع (Navigation Between IOS Modes):**
عشان تنتقل بين الأوضاع دي، بتستخدم أوامر معينة:

- **من User EXEC إلى Privileged EXEC:**
  - استخدم الأمر: `enable`
  - مثال: `Switch> enable` → بياخدك لـ `Switch#`.

![[Pasted image 20250718163856.png]]

- **من Privileged EXEC إلى Global Configuration:**
  - استخدم الأمر: `configure terminal` (أو مختصرها `conf t`).
  - مثال: `Switch# conf t` → بياخدك لـ `Switch(config)#`.



- **من Global Configuration إلى Line Configuration:**
  - استخدم الأمر: `line` متبوع بنوع الاتصال (مثل `line console 0` أو `line vty 0 4`).
  - مثال: `Switch(config)# line console 0` → بياخدك لـ `Switch(config-line)#`.

![[Pasted image 20250718164038.png]]


- **من Global Configuration إلى Interface Configuration:**
  - استخدم الأمر: `interface` متبوع بنوع الواجهة (مثل `interface FastEthernet0/1`).
  - مثال: `Switch(config)# interface FastEthernet0/1` → بياخدك لـ `Switch(config-if)#`.

---
