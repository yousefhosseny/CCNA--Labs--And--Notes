
## 5) Loop Guard — لمنع الـalternate/backup ports من التحول إلى forwarding عند فقدان BPDUs

**الهدف:** في بعض حالات فقدان استقبال BPDUs (مثلاً بسبب unidirectional failure) قد يتحول port كان blocking إلى forwarding ويتسبب في loop. Loop Guard يكشف غياب الـBPDU على non-designated ports ويضعها في حالة **loop-inconsistent blocking** بدل السماح لها بالدخول في forwarding. فعل Loop Guard على inter-switch links/alternate ports يقلّل خطر loops. ([Cisco](https://www.cisco.com/c/en/us/support/docs/lan-switching/spanning-tree-protocol-stp-8021d/218321-configure-stp-with-loop-guard-and-bpdu-s.html?utm_source=chatgpt.com "Understand STP Loop Guard and UDLD Features"))

**أوامر:**

- تفعيل عام:
    

```
spanning-tree loopguard default
```

- أو على واجهة بعينها:
    

```
interface Gi1/0/2
 spanning-tree guard loop
```

**ملاحظة مهمة:** لا تُفعّل Loop Guard على PortFast-enabled (access) ports — صُممت للـblocking/alternate ports بين السويتشات.

---
