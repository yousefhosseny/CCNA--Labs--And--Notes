
### 4. **أنواع بروتوكولات FHRP**
فيه عدة بروتوكولات لتحقيق الـ Redundancy:
1. **HSRP (Hot Standby Router Protocol)**:
   - بروتوكول خاص بسيسكو لتكرار الراوترات في شبكات IPv4.
   - بيختار راوتر نشط (Active) وآخر احتياطي (Standby).
   - يدعم IPv6 بنفس الطريقة مع عنوان MAC وهمي وعنوان Link-Local IPv6.

2. **VRRP (Virtual Router Redundancy Protocol)**:
   - بروتوكول مفتوح (غير خاص بسيسكو) لشبكات IPv4 (VRRPv2) ويدعم IPv4 و IPv6 (VRRPv3).
   - بيختار راوتر رئيسي (Master) وباقي الراوترات بتكون احتياطية.

3. **GLBP (Gateway Load Balancing Protocol)**:
   - بروتوكول خاص بسيسكو زي HSRP، لكن بيسمح بتوزيع الحمل (Load Balancing) بين الراوترات.
   - يدعم IPv4 و IPv6، وكل الراوترات بتشارك في توجيه البيانات مش بس واحد.

4. **IRDP (ICMP Router Discovery Protocol)**:
   - بروتوكول قديم (محدد في RFC 1256) بيسمح للأجهزة بإيجاد راوترات للاتصال بشبكات خارجية.
   - مش شائع زي HSRP أو VRRP.

