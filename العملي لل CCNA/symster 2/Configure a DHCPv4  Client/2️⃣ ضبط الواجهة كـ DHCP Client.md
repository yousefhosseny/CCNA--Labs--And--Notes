
- لو عندك مثلاً واجهة `GigabitEthernet0/0/1` متوصلة بالـ ISP، بتدخل على واجهة الراوتر وتخليها تاخد IP أوتوماتيك.
    

### الخطوات:

```bash
Router> enable                   # ندخل على الـ privileged EXEC mode
Router# configure terminal       # ندخل على وضع الإعدادات
Router(config)# interface g0/0/1 # نختار الواجهة اللي طالعة للـ ISP
Router(config-if)# ip address dhcp # نخليها تاخد IP من DHCP Server
Router(config-if)# no shutdown     # نفعل الواجهة (نفتحها)
```

✅ دلوقتي الراوتر هيبعت **DHCP Discover** عشان يطلب IP من السيرفر.

---
