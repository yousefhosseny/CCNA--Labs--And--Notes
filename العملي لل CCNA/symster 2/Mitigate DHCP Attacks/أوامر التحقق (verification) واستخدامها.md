
# أوامر التحقق (verification) واستخدامها

- تفصيل الوضع العام:
    

```
S1# show ip dhcp snooping
```

يعرض: VLANs المفعّلة، هل الميزة شغالة، قائمة البورتات الموثوقة، وإعدادات الrate.

- جدول الـbinding (مهم جداً — DAI وIP-Source-Guard يعتمدان عليه):
    

```
S1# show ip dhcp snooping binding
```

نموذج مُصغَّر لمخرَج ممكن تشوفه:

```
MacAddress       IpAddress      Lease(sec)  Type           VLAN  Interface
0001.6384.3b2c   192.168.10.15  86399       dhcp-snooping   10    FastEthernet0/5
```

- لمسح الـbindings (لو محتاج تعيد تعيين أثناء troubleshooting):
    

```
S1# clear ip dhcp snooping binding *
```

- لو فعلت persistence لقاعدة البيانات (شبكات متعددة سويتش):
    

```
S1(config)# ip dhcp snooping database tftp://<server>/dhcp_snoop_db
S1# show ip dhcp snooping database
```

(الأمر ده اختياري لكن مفيد لو عايز تخلّي الـbindings متاحة بعد إعادة تشغيل السويتش).

---
