### شبكات OSPF Point-to-Point (نقطة لنقطة)
القسم ده بيتكلم عن تكوين OSPF في روابط مباشرة بين راوترين (point-to-point)، زي روابط WAN أو serial. ده أبسط من الشبكات متعددة الوصول (زي Ethernet)، ومش محتاج انتخاب DR/BDR كتير.

#### أمر Network (لتحديد الواجهات)
- تستخدم `network` عشان تقول لـ OSPF أي واجهات تشارك (ترسل/تستقبل حزم OSPF).
- الصيغة: `network network-address wildcard-mask area area-id`
  - Network-address: عنوان الشبكة.
  - Wildcard-mask: عكس subnet mask (احسبها بـ 255.255.255.255 ناقص subnet mask). مثال:
    - لـ /24 (255.255.255.0): wildcard = 0.0.0.255
    - لـ /26 (255.255.255.192): wildcard = 0.0.0.63
  - Area-id: رقم المنطقة (في single-area، استخدم 0 دايماً عشان سهل لو غيرت لـ multiarea).
- بديل: حدد الواجهة بدقة بـ wildcard 0.0.0.0 (يعني هذه الواجهة بالضبط).

مثال على R1 (بطريقة الشبكة):
```
router ospf 10
network 10.10.1.0 0.0.0.255 area 0  // شبكة كاملة
network 10.1.1.4 0.0.0.3 area 0     // واجهة معينة
```

مثال بديل (بطريقة الواجهة الدقيقة):
```
router ospf 10
network 10.1.1.5 0.0.0.0 area 0  // عنوان الواجهة بالضبط
```

#### تكوين OSPF مباشر على الواجهة (ip ospf)
- بدل `network`، استخدم `ip ospf process-id area area-id` على الواجهة نفسها.
- أول حذف الـ network commands بـ `no network ...`، ثم:
```
interface GigabitEthernet 0/0/0
ip ospf 10 area 0
```
- فائدة: أسهل، مش محتاج تحسب wildcard.

#### Passive Interface (واجهة سلبية)
- بشكل افتراضي، OSPF يرسل رسائل على كل الواجهات النشيطة، حتى لو مش متصلة براوترات أخرى (زي LAN محلية).
- مشكلة: يهدر bandwidth، موارد، وزيادة خطر أمني (يمكن سرقة الرسائل).
- حل: `passive-interface interface-name` في وضع router ospf، عشان تمنع إرسال رسائل، لكن الشبكة لسة تنتشر للآخرين.
- تحقق: `show ip protocols` يظهر الواجهة passive.

مثال:
```
router ospf 10
passive-interface GigabitEthernet 0/0/0  // واجهة LAN، مش محتاج ترسل Hello
```

#### OSPF في Point-to-Point
- افتراضياً، Cisco يعامل الروابط زي broadcast (ينتخب DR/BDR حتى لو راوترين بس).
- تحقق: `show ip ospf interface` يظهر Network Type BROADCAST، وstate BDR أو DR.
- غيرها لـ point-to-point: `ip ospf network point-to-point` على الواجهة.
- فائدة: يمنع انتخاب DR/BDR غير ضروري، ويغير timers (Hello/Dead).

مثال:
```
interface GigabitEthernet 0/0/0
ip ospf network point-to-point
```
- بعد التغيير، الجوار ينخفض مؤقتاً ثم يرجع، وNetwork Type يبقى POINT_TO_POINT.

#### Loopbacks في Point-to-Point
- Loopback افتراضياً ينشر كـ /32 (host route، عنوان واحد).
- لو عايز تنشر الشبكة كاملة (زي /24)، غيرها لـ point-to-point:
```
interface Loopback 0
ip ospf network point-to-point
```
- مثال: قبل: R2 يشوف 10.10.1.1/32. بعد: 10.10.1.0/24.

#### نشاط Packet Tracer
- تكوين عملي: حدد Router IDs، استخدم network بطرق مختلفة على R1/R2/R3، passive interfaces، وتحقق بـ `show ip protocols` و`show ip route`.

باختصار، في point-to-point، ركز على تكوين الواجهات بدقة، اجعلها passive لو مش ضرورية، وغير النوع عشان توفر موارد. ده يخلي OSPF أسرع وأأمن. لو عايز أمثلة كود أكتر أو رسم، قل!