### تعديل OSPFv2 في منطقة واحدة (Modify Single-Area OSPFv2)
القسم ده بيتكلم عن إزاي تغير إعدادات OSPF عشان يشتغل أفضل، خاصة في حساب "التكلفة" (Cost) اللي يحدد أفضل طريق، وكمان تغيير فترات Hello وDead.

#### مقياس OSPF: التكلفة (Cost Metric)
- OSPF يستخدم "التكلفة" كمقياس عشان يختار أفضل طريق (أقل تكلفة = طريق أفضل).
- التكلفة عكسية مع سرعة الواجهة (bandwidth): سرعة أعلى = تكلفة أقل.
- الصيغة: Cost = Reference Bandwidth / Interface Bandwidth (بالـ bps).
- الافتراضي: Reference Bandwidth = 100,000,000 bps (100 Mbps).
- المشكلة: الواجهات السريعة (زي Gigabit أو أعلى) كلها تكلفتها 1، مش يفرق بينهم.
- حلول: غير الـ Reference Bandwidth، أو حدد التكلفة يدوي على الواجهة.

الجدول لتفكيك حساب التكلفة (بالافتراضي، مع تقريب لأقرب عدد صحيح، وأقل قيمة 1):

| نوع الواجهة | Bandwidth (bps) | Cost (100M / Bandwidth) |
|--------------|-----------------|-------------------------|
| Serial (56 Kbps) | 56,000 | 1785 |
| T1 (1.544 Mbps) | 1,544,000 | 64 |
| Ethernet (10 Mbps) | 10,000,000 | 10 |
| Fast Ethernet (100 Mbps) | 100,000,000 | 1 |
| Gigabit Ethernet (1 Gbps) | 1,000,000,000 | 1 |
| 10 Gigabit Ethernet (10 Gbps) | 10,000,000,000 | 1 |

#### تعديل الـ Reference Bandwidth
- غيرها عشان تفرق بين السرعات العالية (مثال: اجعلها 10,000 Mbps لـ 10 Gbps).
- الأمر: `auto-cost reference-bandwidth Mbps` (في وضع router ospf).
- مثال: `auto-cost reference-bandwidth 1000` لـ Gigabit، أو 10000 لـ 10 Gigabit.
- لازم تغيره على كل الراوترات في الشبكة.
- رجع للافتراضي: `auto-cost reference-bandwidth 100`.
- بديل: غير التكلفة على واجهة معينة بـ `ip ospf cost value` (في وضع interface).

الجدول بعد تعديل الـ Reference إلى 10 Gbps (10,000 Mbps):

| نوع الواجهة | Bandwidth (bps) | Cost (10G / Bandwidth) |
|--------------|-----------------|-------------------------|
| Serial (56 Kbps) | 56,000 | 178571 |
| T1 (1.544 Mbps) | 1,544,000 | 6476 |
| Ethernet (10 Mbps) | 10,000,000 | 1000 |
| Fast Ethernet (100 Mbps) | 100,000,000 | 100 |
| Gigabit Ethernet (1 Gbps) | 1,000,000,000 | 10 |
| 10 Gigabit Ethernet (10 Gbps) | 10,000,000,000 | 1 |

- تحقق: `show ip ospf interface` يظهر التكلفة الجديدة.

#### تراكم التكلفة (OSPF Accumulates Cost)
- التكلفة الكلية = مجموع التكاليف من الراوتر للشبكة المقصودة.
- مثال (افترض ref 10G، روابط Gigabit = 10، loopback = 1):
  - R1 لشبكة 10.10.2.0/24 عبر R2: 10 (رابط) + 1 (loopback) = 11.
- تحقق: `show ip route` يظهر [110/11] (110 هو administrative distance، 11 التكلفة).

#### تغيير التكلفة يدوي
- أسباب: تحكم في الطرق (مثل تفضيل طريق معين)، أو توافق مع أجهزة غير Cisco.
- مثال: `interface g0/0/1` ثم `ip ospf cost 30`.

#### اختبار failover (التبديل لطريق احتياطي)
- لو الرابط بين R1 وR2 down، OSPF يستخدم طريق بديل (مثل عبر R3، تكلفة 50).
- تحقق: `show ip route ospf` يظهر الطريق الجديد.

#### فترات Hello وDead
- Hello: يرسل كل 10 ثواني (افتراضي في multiaccess/point-to-point) لعنوان 224.0.0.5.
- Dead: 40 ثانية (4 أضعاف Hello)، لو مفيش Hello، الجار down، ويحدث LSDB.
- مش يرسل على passive interfaces.
- تحقق: `show ip ospf interface` يظهر الفترات، `show ip ospf neighbor` يظهر Dead Time.

#### تعديل الفترات
- غيرها عشان اكتشاف أسرع للفشل (لكن يزيد الترافيك).
- أوامر (على الواجهة): `ip ospf hello-interval seconds`، `ip ospf dead-interval seconds`.
- لازم تتطابق على الراوترين، غير كده الجوار يفقد.
- رجع للافتراضي: `no ip ospf hello-interval` إلخ.
- نصيحة: غير بس لو ضروري، الافتراضي جيد.

#### نشاط Packet Tracer
- غير ref bandwidth لسرعات عالية.
- غير التكلفة.
- غير Hello timers.
- تحقق التغييرات بأوامر show.

باختصار، OSPF يحسب تكلفة بناءً على سرعة، غير الإعدادات عشان يناسب شبكتك، وتحقق دايماً. ده يخلي التوجيه أفضل وأسرع في التعامل مع الفشل. لو عايز مثال كود أو رسم، قل!