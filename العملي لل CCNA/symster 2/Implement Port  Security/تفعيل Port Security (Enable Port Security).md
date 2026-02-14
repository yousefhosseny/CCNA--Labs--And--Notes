
## ⚙️ 2. **تفعيل Port Security (Enable Port Security)**

### 💡 الفكرة:

الـ **Port Security** هي ميزة بتخلي السويتش يراقب الـMAC addresses اللي بتتوصل على كل منفذ.  
يعني المنفذ مش هيسمح إلا بالأجهزة اللي انت محددها أو اللي اتعلمها تلقائيًا كـ"مصرّح بها".

### 🛠️ الخطوات:

1. خليه **Access port** (عشان متوصلش VLANs متعددة زي trunk):
    
    ```bash
    Switch(config-if)# switchport mode access
    ```
    
2. فعّل Port Security:
    
    ```bash
    Switch(config-if)# switchport port-security
    ```
    
3. تأكد:
    
    ```bash
    Switch# show port-security interface fastEthernet 0/1
    ```
    

📋 هيظهرلك مثلاً:

```
Port Security              : Enabled
Port Status                : Secure-up
Violation Mode             : Shutdown
Maximum MAC Addresses      : 1
Sticky MAC Addresses       : None
```

---
