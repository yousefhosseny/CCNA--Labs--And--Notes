
## 1) PortFast — عشان تقلّل زمن الانتظار للـedge hosts

**الهدف:** لما يكون المنفذ متصل بجهاز نهائي (PC, Printer, IP Phone, VM host) نحب المنفذ يدخل فوراً في حالة **forwarding** بدل ما يمر بـlistening/learning (تأخير STP).  
**قواعد مهمة:** PortFast **يُفعل فقط على Access ports** المتصلة بأجهزة نهائية — لا تفعّله على روابط بين سويتشات إلا بحذر شديد لأنها ممكن تسبب loop خطير. ([Cisco](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9500/software/release/17-1/configuration_guide/lyr2/b_171_lyr2_9500_cg/b_171_lyr2_9500_cg_chapter_0101.pdf?utm_source=chatgpt.com "Configuring Optional Spanning-Tree Features"))

**أمثلة أوامر:**

- على Interface واحد:
    

```
conf t
interface GigabitEthernet1/0/10
 switchport mode access
 spanning-tree portfast
```

- تفعيل عام على كل non-trunk (global):
    

```
conf t
spanning-tree portfast default
```

**تحقّق / أوامر مفيدة:**

```
show running-config interface Gi1/0/10
show spanning-tree interface Gi1/0/10 detail
show spanning-tree summary
```

**تحذير عملي:** لا تعمل `spanning-tree portfast` على uplinks بين سويتشات. لو عندك hypervisor أو جهاز بيستخدم virtual switch — افحص topology قبل ما تستخدم `portfast trunk` وفعّله بحذر. ([Reddit](https://www.reddit.com/r/networking/comments/z1v0en/portfast_trunk_best_practice/?utm_source=chatgpt.com "Portfast trunk: best practice. : r/networking"))

---
