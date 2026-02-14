
### **6. تصفية مخرجات الأوامر (Filter Show Command Output):**
- بعض الأوامر (مثل `show running-config`) تُنتج مخرجات طويلة. يمكن تصفيتها باستخدام الرمز **|**:
  - ء  **section**: يعرض القسم بأكمله الذي يبدأ بالتعبير المحدد.
    ```bash
    show running-config | section interface
    ```
  - ء  **include**: يعرض الخطوط التي تحتوي على التعبير.
    ```bash
    show ip interface brief | include up
    ```
  -  ء  **exclude**: يستثني الخطوط التي تحتوي على التعبير.
    ```bash
    show running-config | exclude shutdown
    ```
  -  ء  **begin**: يبدأ العرض من السطر الذي يحتوي على التعبير.
    ```bash
    show ip route | begin 192.168
    ```
- **ضبط عدد الخطوط المعروضة:**
  - الأمر `terminal length 0` يمنع التوقف عند شاشات المخرجات الطويلة:
    ```bash
    R1# terminal length 0
    ```

---

