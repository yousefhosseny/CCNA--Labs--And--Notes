### التحقق من OSPFv2 في منطقة واحدة (Verify Single-Area OSPFv2)
القسم ده بيتكلم عن إزاي تتحقق إن تكوين OSPF في single-area شغال صح. بعد ما تكون الشبكة، استخدم أوامر عشان تشوف الجيران، الطرق، والإعدادات. ده يساعد في اكتشاف المشاكل زي عدم تطابق الإعدادات.

#### أوامر أساسية للتحقق
- **show ip interface brief**: تشوف الواجهات نشيطة ومعها عناوين IP صحيحة.
- **show ip route**: تشوف جدول التوجيه، وإن كل الطرق اللي متوقعة موجودة (O لـ OSPF).

أوامر OSPF الخاصة:
- **show ip ospf neighbor**: تشوف الجيران وحالتهم.
- **show ip protocols**: ملخص الإعدادات.
- **show ip ospf**: معلومات العملية.
- **show ip ospf interface**: تفاصيل الواجهات.

#### تحقق الجيران (Verify OSPF Neighbors)
- الأمر: `show ip ospf neighbor`
- يظهر: Neighbor ID، Priority، State (مثل FULL أو 2-WAY)، Dead Time، عنوان الجار، والواجهة.
- مثال على R1:
  ```
  Neighbor ID Pri State       Dead Time Address     Interface
  3.3.3.3     0   FULL/ -     00:00:35  10.1.1.13  GigabitEthernet0/0/1
  2.2.2.2     0   FULL/ -     00:00:31  10.1.1.6   GigabitEthernet0/0/0
  ```
- لو State مش FULL (أو 2-WAY بين DROTHERs)، مش جيران تمام. أسباب محتملة:
  - Subnet masks مش متطابقة (راوترات في شبكات مختلفة).
  - Hello أو Dead timers مش متطابقة.
  - نوع الشبكة (Network Type) مش متطابق.
  - أمر network غلط أو ناقص.

#### تحقق إعدادات البروتوكول (Verify OSPF Protocol Settings)
- الأمر: `show ip protocols`
- يظهر: Process ID، Router ID، الشبكات المعلنة، الجيران، وadministrative distance (افتراضي 110).
- مثال (مختصر):
  ```
  Routing Protocol is "ospf 10"
  Router ID 1.1.1.1
  Routing for Networks: ... (الواجهات)
  Routing Information Sources: ... (الجيران)
  Distance: 110
  ```

#### تحقق معلومات العملية (Verify OSPF Process Information)
- الأمر: `show ip ospf`
- يظهر: Process ID، Router ID، المناطق، وقت آخر SPF، وإحصائيات LSAs.
- مثال (مختصر):
  ```
  Routing Process "ospf 10" with ID 1.1.1.1
  Area BACKBONE(0)
  Number of interfaces in this area is 3
  SPF algorithm last executed 00:11:31 ago
  ```

#### تحقق إعدادات الواجهات (Verify OSPF Interface Settings)
- الأمر: `show ip ospf interface [interface-name]`
- يظهر: Process ID، Router ID، نوع الشبكة، Cost، DR/BDR (لو multiaccess)، وجيران.
- مثال على G0/0/0:
  ```
  GigabitEthernet0/0/0 ... Area 0
  Network Type POINT_TO_POINT, Cost: 10
  Neighbor Count is 1, Adjacent neighbor count is 1
  Adjacent with neighbor 2.2.2.2
  ```

- ملخص سريع: `show ip ospf interface brief`
  - يظهر: واجهة، PID، Area، عنوان/ماسك، Cost، State، عدد الجيران.
  - مثال:
    | Interface | PID | Area | IP Address/Mask | Cost | State | Nbrs F/C |
    |-----------|-----|------|-----------------|------|-------|----------|
    | Lo0       | 10  | 0    | 10.10.1.1/24    | 10   | P2P   | 0/0      |
    | Gi0/0/1   | 10  | 0    | 10.1.1.14/30    | 30   | P2P   | 1/1      |
    | Gi0/0/0   | 10  | 0    | 10.1.1.5/30     | 10   | P2P   | 1/1      |

#### نشاط Packet Tracer
- تحقق حالة الجيران.
- شوف إزاي الطرق متعلمة.
- شرح حالة الجيران.
- شوف إعدادات Process ID.
- أضف LAN جديدة وتحقق الاتصال.

باختصار، التحقق زي فحص السيارة: شوف الجيران (جاهزين؟)، الإعدادات (متطابقة؟)، والطرق (وصلت؟). لو مش شغال، ابحث عن عدم تطابق. ده يضمن OSPF يعمل بسلاسة. لو عايز مثال عملي أو رسم، قل!