
### 3. **تصنيف بروتوكولات التوجيه الديناميكية (Dynamic Routing Evolution)**
- **بروتوكولات داخلية (Interior Gateway Protocols - IGPs)**:
  - بتستخدم داخل منظمة واحدة (Routing Domain).
  - أنواعها:
    - ال**Distance Vector** (يعتمد على عدد الـ Hops أو المسافة):
      - IPv4: RIPv2، EIGRP
      - IPv6: RIPng، EIGRP for IPv6
    - ال**Link-State** (يعتمد على حالة الروابط):
      - IPv4: OSPFv2، IS-IS
      - IPv6: OSPFv3، IS-IS for IPv6
- **بروتوكولات خارجية (Exterior Gateway Protocols - EGPs)**:
  - زي **BGP** (بروتوكول المسار المتجه - Path Vector):
    - بيستخدم بين منظمات مختلفة (Autonomous Systems)، زي توجيه البيانات عبر الإنترنت بواسطة مزودي الخدمة.

---
