
 **التنقل بين الأوضاع (Navigation Between IOS Modes):**
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

#### 4. **الرجوع للخلف أو الخروج من الأوضاع:**
- **للرجوع خطوة للخلف (للوضع السابق):**
  - استخدم الأمر: `exit`.
  - مثال: من `(config-line)#` بترجع لـ `(config)#`.

- **للرجوع مباشرة لـ Privileged EXEC من أي وضع تهيئة:**
  - استخدم الأمر: `end` أو اضغط **Ctrl + Z**.
  - مثال: من `(config-if)#` بترجع لـ `Switch#`.

- **للتنقل بين أوضاع التهيئة مباشرة:**
  - لو عايز تنتقل من وضع تهيئة (مثل `config-line`) لوضع تهيئة آخر (مثل `config-if`)، اكتب الأمر بتاع الوضع الجديد مباشرة.
  - مثال: من `(config-line)#` اكتب `interface FastEthernet0/1` بياخدك لـ `(config-if)#`.

- **للرجوع من User EXEC إلى الخروج التام:**
  - استخدم الأمر: `disable` (عشان ترجع من `#` لـ `>`).
  - أو `logout` عشان تخرج من النظام.

---

