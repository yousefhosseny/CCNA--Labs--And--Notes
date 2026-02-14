
### 3. **حالات المنافذ في RSTP**
- في STP، كان فيه 5 حالات للمنافذ: Disabled, Blocking, Listening, Learning, Forwarding.
- في RSTP، الحالات اتقلصت لـ 3 حالات فقط:
  - **Discarding**: بيدمج حالات Disabled, Blocking, Listening من STP. المنفذ في الحالة دي مابيمررش بيانات ومابيحدثش جدول الـ MAC.
  - **Learning**: المنفذ بيتعلم عناوين MAC بس مابيمررش بيانات.
  - **Forwarding**: المنفذ بيمرر البيانات وبيحدث جدول الـ MAC.
- **الفرق**: RSTP جمع حالات Disabled, Blocking, Listening في حالة واحدة (Discarding) عشان يبسط العملية ويسرّع التقارب.

---

![[Pasted image 20250908213718.png]]

