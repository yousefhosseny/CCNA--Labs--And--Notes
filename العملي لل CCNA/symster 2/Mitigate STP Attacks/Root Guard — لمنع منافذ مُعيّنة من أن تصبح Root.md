
## 4) Root Guard — لمنع منافذ مُعيّنة من أن تصبح Root

**الهدف:** تحافظ على مكانية الـroot bridge المتفق عليها في التصميم. فعل Root Guard على الـports اللي متصلة بشبكات طرفية أو أجهزة لا يجب أن تصبح root منها يمنع أي BPDU "أفضل" (أدنى priority) من تغيير الـroot — لو استلم المنفذ BPDU يحاول يصبح root، الـport يتحول إلى **root-inconsistent** (يحجب) بدل ما يترك الـroot يتغير. مفيد على uplinks غير مرغوب أن تتغير جذور الشبكة من خلالها. ([Cisco](https://www.cisco.com/c/en/us/support/docs/lan-switching/spanning-tree-protocol/10588-74.html?utm_source=chatgpt.com "Enhance STP with Root Guard"))

**أمر:**

```
interface Gi1/0/1
 spanning-tree guard root
```

**متى أستخدمه؟** على المنافذ التي تربط للسويتشات الطرفية أو الأجهزة التي لا تُفترض أن تكون root. **لا تستخدمه** على منافذ تحتاج أن تتنافس للفوز بالـroot (مثلاً عند تغيّر التصميم).

---
