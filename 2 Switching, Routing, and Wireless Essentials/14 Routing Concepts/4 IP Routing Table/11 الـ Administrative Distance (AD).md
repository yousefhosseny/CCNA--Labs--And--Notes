
### 11. **الـ Administrative Distance (AD)**
- لو الراوتر عرف نفس الشبكة من أكتر من مصدر (مثل Static وOSPF)، بيختار المسار بناءً على **الـ Administrative Distance (AD)**:
  - الـ AD هو مقياس "الثقة" في مصدر المسار. الأقل قيمة هو الأفضل.
  - أمثلة على قيم الـ AD:
    - **Directly Connected**: 0
    - **Static Route**: 1
    - **EIGRP**: 90
    - **OSPF**: 110
    - **RIP**: 120
- يعني لو فيه مسار من OSPF وStatic لنفس الشبكة، الراوتر هيختار الـ Static لأن AD بتاعه أقل (1 أحسن من 110).

---
