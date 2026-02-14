
### 7. **CDP Reconnaissance**
- **CDP (Cisco Discovery Protocol)**: بروتوكول خاص بسيسكو بيبعت معلومات عن الأجهزة (زي عنوان IP، إصدار IOS، الـ Native VLAN) بشكل دوري وغير مشفر.
- المهاجم بيقدر يجمع المعلومات دي عشان يخطط لهجمات.
- **الحل**:
  - تعطيل CDP على مستوى الجهاز بأمر: `no cdp run`.
  - تعطيل CDP على منفذ معين بأمر: `no cdp enable`.
  - تعطيل **LLDP** (بروتوكول مشابه) بأوامر: `no lldp run` (عام) أو `no lldp transmit` و `no lldp receive` (على المنفذ).

