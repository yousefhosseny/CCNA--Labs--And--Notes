
### 3. **حلول التصدي لهجمات الطبقة الثانية (Switch Attack Mitigation Techniques)**
عشان نحمي الطبقة الثانية، بنستخدم الحلول دي:
- **Port Security**: بيمنع هجمات زي MAC Address Flooding و DHCP Starvation بتحديد عدد عناوين MAC المسموح بيها على منفذ الـ Switch.
- **DHCP Snooping**: بيحمي من هجمات DHCP Starvation و Spoofing عن طريق تصفية رسائل DHCP والسماح بس من سيرفرات موثوقة.
- **Dynamic ARP Inspection (DAI)**: بيمنع هجمات ARP Spoofing و Poisoning عن طريق التحقق من صحة رسائل ARP.
- **IP Source Guard (IPSG)**: بيمنع تزييف عناوين MAC و IP بفحص مصدر الـ Packets.
