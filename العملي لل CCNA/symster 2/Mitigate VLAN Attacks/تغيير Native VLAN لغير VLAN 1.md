
## 5) تغيير Native VLAN لغير VLAN 1

**ليه؟**  
هجوم الـ double-tagging يستغل أن الـ native VLAN عادة بتكون بدون tag (VLAN 1). بتغيير native VLAN لرقم غير مستخدم، وتأكيد أن الـ native VLAN **مُعنوَن** (tagged) على الطرفين، تقلل هجمة الـ VLAN hopping.

**أمر:**

```shell
interface GigabitEthernet0/48
  switchport trunk native vlan 99
```

**تحسين إضافي (أفضل ممارسة):** جعل Native VLAN مُعلّمة دومًا على كل الـ trunks (تجبر وضع tag حتى للـ native VLAN) — أمر عالمي على بعض الأجهزة:

```shell
conf t
vlan dot1q tag native
exit
```

(هذا يمنع frames بدون tag ويقلل double-tagging attacks)

**تأكيد/فحص:**

```shell
show interfaces trunk
show running-config interface GigabitEthernet0/48
show interfaces GigabitEthernet0/48 switchport
```

---
