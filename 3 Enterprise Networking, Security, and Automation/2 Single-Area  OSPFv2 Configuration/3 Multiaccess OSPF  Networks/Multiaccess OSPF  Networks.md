### شبكات OSPF متعددة الوصول (Multiaccess OSPF Networks)
القسم ده بيتكلم عن OSPF في شبكات زي Ethernet، اللي تربط كتير راوترات على رابط واحد (multiaccess). هنا، OSPF ينتخب راوتر رئيسي (DR) عشان يدير تبادل الـ LSAs (إعلانات حالة الروابط) ويقلل الفوضى، مش زي point-to-point اللي مش محتاج ده.

#### نوع الشبكة
- في multiaccess، راوتر واحد (DR) يتحكم في توزيع LSAs. الإداري يحدد ده بتكوين صحيح.

#### الـ Designated Router (DR) و BDR
- ال**DR**: الرئيسي، يجمع ويوزع LSAs لكل الراوترات. يرسل لعنوان multicast 224.0.0.5 (كل OSPF routers).
- ال**BDR**: المساعد، يسمع بس ويحافظ على علاقات. لو DR فشل، يصير DR.
- ال**DROTHER**: الباقي (مش DR أو BDR). يرسلوا لـ 224.0.0.6 (كل DR/BDR)، وDR/BDR بس اللي يسمعوا.

#### توبولوجي مرجعي (Reference Topology)
- مثال: 3 راوترات (R1، R2، R3) متصلة على شبكة Ethernet 192.168.1.0/24.
- OSPF انتخب DR: R3 (أعلى ID 3.3.3.3)، BDR: R2 (ثاني أعلى 2.2.2.2).

#### تحقق من الأدوار (Verify OSPF Router Roles)
استخدم `show ip ospf interface` عشان تشوف الدور:
- R1: DROTHER (priority 1)، DR هو R3، BDR هو R2، adjacencies مع DR وBDR.
- R2: BDR (priority 1)، DR هو R3، adjacencies مع R1 وDR.
- R3: DR (priority 1)، BDR هو R2، adjacencies مع R1 وBDR.

مثال إخراج لـ R1 (مختصر):
```
GigabitEthernet0/0/0 ... State DROTHER, Priority 1
Designated Router (ID) 3.3.3.3 ...
Backup Designated router (ID) 2.2.2.2 ...
Adjacent with neighbor 2.2.2.2 (Backup Designated Router)
Adjacent with neighbor 3.3.3.3 (Designated Router)
```

#### تحقق من الجوار (Verify DR/BDR Adjacencies)
استخدم `show ip ospf neighbor`:
- الحالات: FULL/DROTHER (مع غير DR/BDR)، FULL/DR (مع DR)، FULL/BDR (مع BDR)، 2-WAY/DROTHER (بين DROTHERs، بس Hello).
- عادي FULL، أو 2-WAY في multiaccess.
- مثال على R2:
```
Neighbor ID Pri State       Dead Time Address      Interface
1.1.1.1     1   FULL/DROTHER 00:00:31 192.168.1.1 GigabitEthernet0/0/0
3.3.3.3     1   FULL/DR      00:00:34 192.168.1.3 GigabitEthernet0/0/0
```

#### عملية انتخاب DR/BDR الافتراضية
بناءً على:
1. **أولوية الواجهة (Priority)**: أعلى priority (0-255) يبقى DR، ثاني BDR. افتراضي 1، لو 0 مش ينتخب.
2. **لو متساوية، أعلى Router ID**: يحدد DR وBDR.
- الانتخاب يحصل لما أول راوتر يشتغل، مش يتغير لو جاء جديد.
- لو DR فشل، BDR يصير DR، ثم ينتخب BDR جديد.

#### فشل DR واستعادة
- لو DR فشل (أو OSPF توقف أو الواجهة down)، BDR يصير DR.
- بعد كده، ينتخب BDR جديد (أعلى priority أو ID من DROTHERs).

#### أمر ip ospf priority
- غير priority على الواجهة: `ip ospf priority value` (0-255).
- أفضل تحكم بالـ priority بدل الاعتماد على ID.
- مثال: اجعل R1 أولوية 255، ثم `clear ip ospf process` عشان يعاد الانتخاب.

#### نشاط Packet Tracer
- شوف أدوار DR/BDR وتغييرها لو في تغيير شبكة.
- غير priority عشان تتحكم في الانتخاب.
- تحقق إن الراوترات في الأدوار المرغوبة.

باختصار، في multiaccess، DR وBDR ينظموا التحديثات عشان مش كل راوتر يرسل للكل، ده يوفر موارد. الإداري يتحكم بالانتخاب عشان أفضل أداء. لو عايز تفاصيل أكتر أو رسم، قل!