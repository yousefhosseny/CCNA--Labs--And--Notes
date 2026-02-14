
## 1) تعطيل DTP على المنافذ غير الـ trunk

**ليه؟**  
DTP (Dynamic Trunking Protocol) بيتفاوض تلقائيًا لتحويل ال port إلى trunk. لو سيبت التفاوض شغال، مهاجم ممكن يخدع السويتش ويخلي الport يبقى trunk ويعمل VLAN hopping.

**أمر أساسي:**

```shell
interface GigabitEthernet0/3
  switchport mode access
```

**مثال لعدة منافذ:**

```shell
conf t
interface range GigabitEthernet0/1 - 24
  switchport mode access
  switchport access vlan 10
  description Access_ports_to_users
  spanning-tree portfast
exit
```

**تأكيد/فحص:**

```shell
show interfaces GigabitEthernet0/3 switchport
# راجع: "Administrative Mode: static access" و "Negotiation of Trunking: Off"
show vlan brief
```

**ملاحظة:** كفاية إنك تعمل `switchport mode access` لأن ده يمنع DTP من محاولة عمل trunk.

---
