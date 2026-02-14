
### 6. **LACP (Link Aggregation Control Protocol)**
- بروتوكول IEEE قياسي، يعني بيشتغل مع أجهزة غير Cisco.
- زي PAgP، بيبعت حزم عشان يتفاوض ويتأكد إن الروابط متوافقة.
- **أوضاع LACP**:
  -  ء **On**: يجبر المنفذ على تكوين EtherChannel بدون تفاوض.
  - ء  **Active**: المنفذ بيبدأ التفاوض بنشاط بإرسال حزم LACP.
  -  ء **Passive**: المنفذ بيستجيب لحزم LACP بس مابيبدأش التفاوض.
- **جدول توافق أوضاع LACP**:
  | **S1**       | **S2**       | **النتيجة** |
  |--------------|--------------|-------------|
  | On           | On           | نعم (يتكون) |
  | On           | Active/Passive | لا         |
  | Active       | Active       | نعم        |
  | Active       | Passive      | نعم        |
  | Passive      | Active       | نعم        |
  | Passive      | Passive      | لا         |

![[Pasted image 20250908213934.png]]

