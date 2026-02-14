
---

### 2) فعّلها على VLANs المطلوبة

الأمر:

```
Switch(config)# ip dhcp snooping vlan 5,10,50-52
```

**ليه؟** Snooping بيشتغل على فيلانز محددة؛ لو ما فعلتهاش على VLAN معينة مفيش حماية هناك. فعّلها على كل VLAN اللي فيها عملاء أو DHCP traffic.

---
