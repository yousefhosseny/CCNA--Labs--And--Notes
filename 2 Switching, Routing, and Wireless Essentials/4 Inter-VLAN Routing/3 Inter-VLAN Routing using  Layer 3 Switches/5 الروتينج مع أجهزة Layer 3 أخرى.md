
### 5. **الروتينج مع أجهزة Layer 3 أخرى**
- لو عايز الـ VLANs تبقى متاحة لأجهزة Layer 3 أخرى (زي راوتر R1)، لازم تعلن عن الشبكات باستخدام **روتينج ديناميكي** (زي OSPF) أو **روتينج ستاتيك**.
- **Routed Port**:
  - لو عايز تربط الـ Layer 3 Switch بجهاز Layer 3 تاني (زي راوتر)، لازم تحول منفذ في السويتش من Layer 2 لـ Layer 3 (Routed Port) بأمر:
    ```
    D1(config)# interface g0/0/1
    D1(config-if)# no switchport
    D1(config-if)# ip address 10.10.10.2 255.255.255.0
    D1(config-if)# no shutdown
    D1(config-if)# end
    ```
  - الأمر `no switchport` بيحول المنفذ من Switchport (Layer 2) لـ Routed Port (Layer 3) زي منفذ الراوتر.

---

### الشرح للجزء  : من الدقيقه ال 00:00:00 الي الدقيقه  00:00:00


