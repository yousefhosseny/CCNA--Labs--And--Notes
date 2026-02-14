
### **3. خاصية Auto-MDIX:**
- **Auto-MDIX** (Automatic Medium-Dependent Interface Crossover) تتيح للمحول اكتشاف نوع الكابل (Straight-Through أو Crossover) تلقائيًا وتعديل الاتصال.
- مع تفعيل Auto-MDIX، يمكن استخدام أي نوع كابل (لا حاجة للقلق بشأن نوع الكابل).
- **كيفية التفعيل:**
  - تكون مفعلة افتراضيًا في محولات Cisco الحديثة (مثل Catalyst 2960 و3560).
  - يجب ضبط السرعة وDuplex على **Auto** ليعمل Auto-MDIX.
  - الأمر:
    ```bash
    S1(config-if)# mdix auto
    ```
- للتحقق من إعداد Auto-MDIX:
  ```bash
  S1# show controllers ethernet-controller <interface-id> phy | include Auto-MDIX
  ```

---
