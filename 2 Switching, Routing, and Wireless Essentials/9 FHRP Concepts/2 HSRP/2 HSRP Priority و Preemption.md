
### 2. **HSRP Priority و Preemption**
- **Priority (الأولوية)**:
  - بيحدد مين هيبقى الـ Active Router. الراوتر اللي عنده أعلى Priority بيبقى الـ Active.
  - الـ Priority الافتراضي هو 100، والنطاق من 0 إلى 255.
  - لو الـ Priority متساوي عند راوترين، اللي عنده عنوان IPv4 أعلى بيبقى الـ Active.
  - الأمر لضبط الـ Priority: `standby priority [value]` (مثال: `standby 1 priority 150`).
- **Preemption**:
  - لو مفعّل، راوتر جديد عنده Priority أعلى بيقدر ياخد مكان الـ Active Router لو دخل الشبكة.
  - الأمر لتفعيل Preemption: `standby preempt`.
  - بدون Preemption، الراوتر اللي بقى Active هيفضل Active حتى لو جه راوتر بـ Priority أعلى، طالما هو شغال.
  - ملاحظة: لو الـ Priority متساوي، عنوان IPv4 أعلى مش هيخلّي الراوتر ياخد مكان الـ Active لو Preemption مفعّل.

![[Pasted image 20250908215332.png]]

