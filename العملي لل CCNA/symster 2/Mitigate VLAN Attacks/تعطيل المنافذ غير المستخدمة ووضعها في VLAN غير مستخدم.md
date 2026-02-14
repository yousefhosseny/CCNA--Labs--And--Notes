
## 2) تعطيل المنافذ غير المستخدمة ووضعها في VLAN غير مستخدم

**ليه؟**  
منافذ فاضية بتكون هدف سهل للهكر لو حد وصل جهاز. إغلاقها (administratively down) أو على الأقل وضعها في VLAN آمن يقلل الهجوم.

**أوامر نموذجية:**

```shell
vlan 999
 name UNUSED_PORTS

interface range GigabitEthernet0/25 - 48
  description UNUSED - SHUTDOWN
  switchport mode access
  switchport access vlan 999
  shutdown
exit
```

**تأكيد/فحص:**

```shell
show interface status | include Gi0/25
show running-config interface GigabitEthernet0/25
show vlan brief | include 999
```

**ملاحظة:** لو مينفعش تغلق المنفذ (مثلاً لإدارة عن بعد من خلال كيبل)، بدّلها لـ `no shutdown` لكن خليها في VLAN غير مستخدم وفعّل port-security وspanning-tree portfast+bpduguard.

---
