### نشر الطريق الافتراضي في OSPFv2 (Default Route Propagation)
القسم ده بيتكلم عن إزاي تخلي راوتر OSPF ينشر "طريق افتراضي" (default route) للآخرين، عشان يوصلوا لأي مكان خارج الشبكة (زي الإنترنت). ده مهم لو الشبكة متصلة بالخارج عبر راوتر واحد (edge router).

#### خطوات التكوين
عشان تنشر default route، الراوتر الحدودي (مثل R2 في المثال) لازم يعمل كده:
1. **تكوين طريق static default**: `ip route 0.0.0.0 0.0.0.0 [next-hop-address | exit-intf]`
   - ده يقول للراوتر: "أي عنوان مش معروف، روح من هنا".
   - نصيحة: استخدم next-hop IP لو موجود، لكن لو محاكاة إنترنت (زي loopback)، استخدم exit-intf.

2. **نشرها في OSPF**: في وضع `router ospf process-id`، أضف `default-information originate`.
   - ده يخلي الراوتر يرسل الطريق ده لكل الراوترات التانية في OSPF.

مثال على R2 (مع loopback1 كمحاكاة للإنترنت):
```
interface lo1
ip address 64.100.0.1 255.255.255.252
exit
ip route 0.0.0.0 0.0.0.0 loopback1  // default route
router ospf 10
default-information originate
```

#### تحقق من الطريق (Verify)
- على R2: `show ip route` يظهر S* (static default) متصل مباشرة بلوبباك.
- على الراوترات التانية (زي R1 وR3): `show ip route` يظهر O*E2 (OSPF external default)، مع [110/1] (110 administrative distance، 1 تكلفة افتراضية).
  - O*E2: طريق خارجي من OSPF، * يعني default.

مثال إخراج:
- R2: S* 0.0.0.0/0 متصل بلوبباك.
- R1: O*E2 0.0.0.0/0 عبر 10.1.1.6.

(ملاحظة: E2 يعني external type 2، E1 type 1، بس ده خارج النطاق هنا.)

#### نشاط Packet Tracer
- جزء 1: نشر الطريق الافتراضي زي فوق.
- جزء 2: تحقق الاتصال (ping أو traceroute للخارج).

باختصار، الطريق الافتراضي زي "الباب الرئيسي" للإنترنت، تنشره عشان كل الراوترات تعرفه بدون تكوين يدوي. ده يوفر وقت ويخلي الشبكة سهلة الإدارة. لو عايز مثال عملي أو رسم، قل!