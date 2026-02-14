
### 2. **LLA الديناميكية على Windows**:
- أنظمة التشغيل زي Windows بتستخدم نفس الطريقة لتوليد الـ **Interface ID** لكل من الـ GUA والـ LLA.
- أمثلة من أمر `ipconfig`:
  - **EUI-64**:
    ```
    IPv6 Address: 2001:db8:acad:1:fc99:47ff:fe75:cee0
    Link-local IPv6 Address: fe80::fc99:47ff:fe75:cee0
    Default Gateway: fe80::1
    ```
    - الـ Interface ID (`fc99:47ff:fe75:cee0`) مبني على عنوان MAC.
  - **توليد عشوائي**:
    ```
    IPv6 Address: 2001:db8:acad:1:50a5:8a35:a5bb:66e1
    Link-local IPv6 Address: fe80::50a5:8a35:a5bb:66e1
    Default Gateway: fe80::1
    ```
    - الـ Interface ID (`50a5:8a35:a5bb:66e1`) مولّد عشوائيًا (زي اللي بتعمله Windows من Vista وطالع).


![[Pasted image 20250808201821.png]]
