
## 2) BPDU Guard — طريقة سريعة لإيقاف محاولات إدخال سويتش غير مصرح به

**الهدف:** لو أي access port متوقع عليه جهاز نهائي استلم BPDU (يعني حد وصل سويتش أو بعت BPDUs) — نوقفه فوراً (error-disabled) لمنع تشكيل loops أو takeover للشجرة. BPDU Guard يعطي رد فعل فوري عندما يأتي BPDU على PortFast-enabled port. ([Cisco](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9200/software/release/16-12/configuration_guide/lyr2/b_1612_lyr2_9200_cg/configuring_optional_spanning_tree_features.html?utm_source=chatgpt.com "Layer 2 Configuration Guide, Cisco IOS XE Gibraltar 16.12. ..."))

**أمثلة أوامر:**

- على interface واحد:
    

```
conf t
interface Gi1/0/10
 spanning-tree bpduguard enable
```

- تفعيل عام لكل الـportfast ports:
    

```
conf t
spanning-tree portfast bpduguard default
```

**سلوك عند حدوث BPDU:** المنفذ يُصبح **err-disabled** (مغلق) فوراً. هذا يمنع الـport من المشاركة في STP ويمنع loop. ([Cisco](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9200/software/release/16-12/configuration_guide/lyr2/b_1612_lyr2_9200_cg/configuring_optional_spanning_tree_features.html?utm_source=chatgpt.com "Layer 2 Configuration Guide, Cisco IOS XE Gibraltar 16.12. ..."))

**استرجاع المنفذ (Recovery):**

- **يدوياً (مُوصى به قبل التلقائي):**
    

```
interface Gi1/0/10
 shutdown
 no shutdown
```

- **أوتوماتيكياً (إذا قررت تسمح بمحاولات تلقائية للرفع بعد وقت):**
    

```
conf t
errdisable recovery cause bpduguard
errdisable recovery interval 300    ! بالثواني (مثال: 5 دقائق)
```

> نصيحة مهمة: قبل تفعّل الـ`errdisable recovery` لفترات قصيرة، تأكّد إنك حلّلت سبب الـBPDU (جهاز غير مصرح؟ كابل وصل لسويتش آخر؟). لو المشكلة متكررة، التشغيل التلقائي ممكن يعيد فتح منفذ يتعرّض لهجوم مستمر. ([Cisco](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9300/software/release/17-8/command_reference/b_178_9300_cr/interface_and_hardware_commands.html?utm_source=chatgpt.com "Command Reference, Cisco IOS XE Cupertino 17.8.x ..."))

**تأكد من الحالة:**

```
show interface status err-disabled
show errdisable recovery
show logging
```

---
