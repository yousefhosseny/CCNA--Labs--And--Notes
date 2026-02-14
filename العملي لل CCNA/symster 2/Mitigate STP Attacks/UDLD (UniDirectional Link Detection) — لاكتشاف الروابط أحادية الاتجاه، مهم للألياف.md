
## 6) UDLD (UniDirectional Link Detection) — لاكتشاف الروابط أحادية الاتجاه، مهم للألياف

**الهدف:** يكتشف لو الكابل/الترانسمت أو الريسيف في طرف واحد اتقطعا — UDLD يرسل رسائل بين الجهتين، ولو لم يستقبل الرد يضع المنفذ في حالة خطأ (يمكن وضعه في err-disable في الـaggressive mode). مهم جداً على fiber links حيث أخطاء في التوصيل تسبب loops. ([Cisco](https://www.cisco.com/c/en/us/support/docs/lan-switching/unidirectional-link-detection-udld/217977-configure-the-udld-protocol-feature.html?utm_source=chatgpt.com "Configure the UDLD Protocol Feature - Cisco"))

**أوامر أمثلة:**

- تفعيل للمنفذ:
    

```
interface TenGigabitEthernet1/1/1
 udld port aggressive
```

- أو تشغيل UDLD عام (platform dependent):
    

```
udld enable
```

**تحذير:** نمط aggressive يوفّر إيقافاً أقوى لكنه قد يعطل منافذ لو هناك مشاكل مادية حقيقية — افحص الملاحظات والـlogs.

---
