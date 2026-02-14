### 1. إعطاء الجهاز اسم
```bash
en
conf t
  hostname [اسم الجهاز]
  ```
### 2. لإلغاء الاسم والرجوع للاسم الافتراضي

```bash
en
conf t
  no hostname
  ```
    
### 3.  تهيئة كلمات المرور 

- 
	- **تأمين User EXEC Mode (وصول الكونسول):**
	
![[Recording 20250802024038.m4a]]

```bash
	en
	conf t
     line console 0
     password [كلمة المرور]
     login
     end
     ```

- - **تأمين Privileged EXEC Mode:**

![[Recording 20250802024247.m4a]]

```bash
	en
	conf t
     

enable secret [كلمة المرور]
     login
     end
     ```

- - **تأمين VTY Lines (الوصول عن بُعد عبر Telnet/SSH):**
```bash
	en
	conf t
     line vty 0 15
      password [كلمة المرور]
     login
     end
     ```
 
### 4.  تشفير كلمات المرور
 بعد م اعمل خطوه ال password اعمل الخطوه دي يعني لازم اعمل خطوه ( تهيئة ال password  ) الاول
 
```bash
	en
	conf t
     service password-encryption
     exit
     show running-config
     ```
 
### 5.  انشاء رسائل التحذير

 ```bash
 en
 conf t  
  banner motd # [الرسالة] #
  ```


#### لاب عملي علي الجزء ده 

اللاب اهو

حل اللاب اهو
