
#### 4. **حفظ الإعدادات في ملف نصي (Capture Configuration to a Text File):**
- ممكن تحفظ الإعدادات (running-config أو startup-config) في ملف نصي للأرشفة:
  1. افتح برنامج زي **PuTTY** أو **Tera Term** واتصل بالجهاز.
  2. فعّل خاصية التسجيل (Logging) في البرنامج، وحدد اسم ومكان الملف (مثل `MySwitchLogs`).
![[Pasted image 20250718172024.png]]

  3. نفّذ أمر:
     ```
     show running-config
     ```
     أو
     ```
     show startup-config
     ```
     (الناتج هيتسجل في الملف).
![[Pasted image 20250718172043.png]]

  4. أوقف التسجيل في البرنامج.
- **ملاحظة:** الملف النصي ده ممكن تحتاج تعدله لو عايز تستخدمه لاستعادة الإعدادات.

![[Pasted image 20250718172057.png]]

---
