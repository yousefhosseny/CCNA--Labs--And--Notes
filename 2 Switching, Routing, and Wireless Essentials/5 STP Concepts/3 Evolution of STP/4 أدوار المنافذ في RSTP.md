
### 4. **أدوار المنافذ في RSTP**
- أدوار المنافذ الرئيسية (Root Port وDesignated Port) زي STP بالظبط:
  - **Root Port**: المنفذ اللي بيوفر أقل تكلفة للـ Root Bridge.
  - **Designated Port**: المنفذ اللي بيمرر البيانات على رابط بين سويتشين.
- بس RSTP عنده أدوار إضافية للمنافذ اللي كانت في حالة Blocking في STP:
  - **Alternate Port**: منفذ بيوفر مسار بديل للـ Root Bridge. لو حصل عطل، بيقدر يتحول لـ Forwarding فورًا.
  - **Backup Port**: منفذ احتياطي في حالة وجود رابط مشترك (زي Hub، وده نادر دلوقتي لأن الـ Hubs بقت قديمة).

---


![[Pasted image 20250908213642.png]]

