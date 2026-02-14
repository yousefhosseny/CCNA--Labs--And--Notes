
### **6. مشاكل طبقة الوصول إلى الشبكة (Network Access Layer Issues):**
- **التحقق باستخدام `show interfaces`:**
  - ء  **FastEthernet0/18 is up, line protocol is up**: المنفذ يعمل بشكل صحيح.
  - ء  **FastEthernet0/18 is up, line protocol is down**: مشكلة في طبقة الرابط (مثل عدم تطابق Encapsulation أو مشكلة في الساعة).
  - ء  **FastEthernet0/18 is down, line protocol is down**: الكابل غير موصول أو المنفذ معطل.
  -  ء  **Administratively down**: المنفذ معطل يدويًا بأمر `shutdown`.

- **أنواع الأخطاء الشائعة:**
  - ء   **Input Errors**: مجموع الأخطاء في الحزم المستلمة (تشمل Runts، Giants، CRC).
    - ء  **Runts**: حزم أصغر من 64 بايت (بسبب خلل في بطاقة الشبكة أو تصادمات).
    - **Giants**: حزم أكبر من 1518 بايت.
    - ء  **CRC Errors**: أخطاء في فحص الحزم (بسبب تداخل كهربائي أو كابل تالف).
  - ء  **Output Errors**: أخطاء في إرسال الحزم.
    - ء   **Collisions**: تحدث في Half-Duplex (طبيعي)، لكنها غير مقبولة في Full-Duplex.
    - ء **Late Collisions**: تصادمات تحدث بعد إرسال 512 بت (بسبب كابل طويل جدًا أو عدم تطابق Duplex).

---

