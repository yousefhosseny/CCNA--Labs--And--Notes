
## 3) BPDU Filter — استخدمها بحذر (قد تعادل تعطيل STP على المنفذ)

**الهدف:** تمنع إرسال واستقبال BPDUs على المنفذ — مفيدة فقط في حالات خاصة (مثلاً أجهزة نهائية تحتاج ألا ترى BPDUs).  
**تحذير كبير:** تفعيل BPDU Filter على Interface يعادل عملياً **إيقاف STP على ذلك المنفذ** — قد ينتج عنه loops إن وصّلت سويتش هناك. على global level، PortFast-enabled ports لا ترسل/تستقبل BPDUs بعد تأثير الـinit، لكن لو استلمت BPDU تفقد الـPortFast وتعود كـSTP port عادي. استخدم BPDU-filter بحذر وبعد فهم التبعات. ([Cisco](https://www.cisco.com/en/US/docs/switches/metro/me3600x_3800x/trash/swstpopt.html?utm_source=chatgpt.com "Configuring Optional Spanning-Tree Features [Support]"))

**أوامر:**

- واجهة:
    

```
interface Gi1/0/10
 spanning-tree bpdufilter enable
```

- عام (على كل portfast ports):
    

```
spanning-tree portfast bpdufilter default
```

---
