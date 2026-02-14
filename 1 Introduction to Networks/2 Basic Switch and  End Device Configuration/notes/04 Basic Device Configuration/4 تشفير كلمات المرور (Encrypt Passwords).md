
#### 4. **تشفير كلمات المرور (Encrypt Passwords):**
- بشكل افتراضي، كلمات المرور بتظهر كنص عادي في ملفات الإعداد (`running-config` أو `startup-config`).
- عشان تشفّر كل كلمات المرور:
  - استخدم الأمر:
    ```
    service password-encryption
    ```

![[Pasted image 20250718170736.png]]

- للتحقق من التشفير:
  - اكتب:
    ```
    show running-config
    ```
  - هتشوف كلمات المرور مشفرة (مش كنص عادي).

![[Pasted image 20250718170751.png]]


---
