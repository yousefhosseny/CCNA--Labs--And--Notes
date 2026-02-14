
2. **فعل DHCP Snooping على VLANs محددة**  
    ليه: مش لازم تفعلها على كل VLANs — فعلها على VLANs اللي فيها عملاء ديناميك/مستخدمين.  
    أمر (مثال VLANs 10 و 20):
    
    ```
    Switch(config)# ip dhcp snooping vlan 10,20
    ```
    
