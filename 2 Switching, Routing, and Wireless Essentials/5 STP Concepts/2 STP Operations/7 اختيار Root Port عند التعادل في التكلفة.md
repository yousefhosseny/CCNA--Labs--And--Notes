
### 7. **اختيار Root Port عند التعادل في التكلفة**
لو فيه مسارات متعادلة التكلفة للـ Root Bridge، STP بيختار بناءً على:
1. **أقل Sender BID**: السويتش اللي بيبعت الـ BPDU وله أقل BID، منفذه هيبقى الـ Root Port.
2. **أقل Sender Port Priority**: لو الـ BID متعادل، بيختار المنفذ اللي عنده أولوية أقل (الافتراضي 128).
3. **أقل Sender Port ID**: لو الأولوية متعادلة، بيختار المنفذ اللي رقم ID بتاعه أقل (مثل F0/1 أقل من F0/2).
- **مثال**:
  - S2 عنده مسارين للـ Root Bridge بنفس التكلفة. لو S4 عنده BID أقل من S3، المنفذ في S2 اللي متصل بـ S4 هيبقى الـ Root Port.

---
 **أقل Sender BID**
![[Pasted image 20250908213520.png]]

 **أقل Sender Port Priority**
![[Pasted image 20250908213537.png]]

**أقل Sender Port ID**
![[Pasted image 20250908213552.png]]

