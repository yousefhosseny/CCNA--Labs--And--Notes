
```text
! Exclude
ip dhcp excluded-address 192.168.1.1 192.168.1.10

! Pool
ip dhcp pool OFFICE
 network 192.168.1.0 255.255.255.0
 default-router 192.168.1.1
 dns-server 8.8.8.8 8.8.4.4
 domain-name company.local
 lease 7

! Static reservation (مثال)
ip dhcp pool PRINTER
 address 192.168.1.50 hardware-address 0011.2233.4455
 default-router 192.168.1.1

! Relay (if server remote)
interface Vlan10
 ip address 192.168.10.1 255.255.255.0
 ip helper-address 192.168.11.6

! Verification
show running-config | section dhcp
show ip dhcp pool
show ip dhcp binding
show ip dhcp server statistics
debug ip dhcp server packet
```

---
