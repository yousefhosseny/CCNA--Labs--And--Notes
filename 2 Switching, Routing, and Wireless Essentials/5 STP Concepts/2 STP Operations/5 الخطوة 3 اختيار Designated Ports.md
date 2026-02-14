
### 5. **الخطوة 3: اختيار Designated Ports**
- كل رابط (Segment) بين سويتشين لازم يكون ليه منفذ واحد بس بيمرر البيانات، وده الـ **Designated Port**.
- الـ Designated Port هو المنفذ اللي عنده أقل تكلفة للوصول للـ Root Bridge.
- **قواعد**:
  - كل منافذ الـ Root Bridge هي Designated Ports.
  - لو طرف الرابط هو Root Port، الطرف التاني هيبقى Designated Port.
  - على رابط بين سويتشين مش Root Bridge، المنفذ اللي عنده أقل تكلفة للـ Root Bridge بيبقى Designated.
  - لو التكلفة متعادلة، السويتش اللي عنده أقل BID بياخد الـ Designated Port.
- **مثال**:
  - بين S2 وS3، لو S3 عنده تكلفة أقل (مثل 4 مقابل 19)، منفذ F0/2 في S3 هيبقى Designated، ومنفذ F0/2 في S2 هيتحجب.

---

![[Pasted image 20250908213248.png]]


![[Pasted image 20250908213304.png]]
