
#### 3. **تهيئة كلمات المرور (Configure Passwords):**

- **تأمين User EXEC Mode (وصول الكونسول):**
  1. ادخل وضع تهيئة الكونسول:
     ```
     line console 0
     ```
  2. ضع كلمة المرور:
     ```
     password [كلمة المرور]
     ```
     مثال: `password cisco`
  3. فعّل كلمة المرور:
     ```
     login
     ```

![[Pasted image 20250718170612.png]]


- **تأمين Privileged EXEC Mode:**
  1. ادخل وضع Global Configuration:
     ```
     configure terminal
     ```
  2. ضع كلمة المرور:
     ```
     enable secret [كلمة المرور]
     ```
     مثال: `enable secret class`

![[Pasted image 20250718170624.png]]


- **تأمين VTY Lines (الوصول عن بُعد عبر Telnet/SSH):**
  1. ادخل وضع تهيئة VTY:
     ```bash
 line vty 0 15
     ```
     (الرقم من 0 إلى 15 لأن معظم سويتشات Cisco تدعم حتى 16 خط VTY).
  3. ضع كلمة المرور:
     ```
     password [كلمة المرور]
     ```
     مثال: `password cisco`
  4. فعّل كلمة المرور:
     ```
     login
end
     ```

![[Pasted image 20250718170700.png]]

---





