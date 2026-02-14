### 4. **نتايج إعدادات DTP**
الجدول ده بيوضح إيه اللي بيحصل لما تدمج بين أوضاع DTP على منفذين بين سويتشين:

| **وضع المنفذ 1** | **وضع المنفذ 2**       | **النتيجة**            |
|-------------------|-------------------------|-------------------------|
| Dynamic Auto      | Dynamic Auto            | Access                 |
| Dynamic Auto      | Dynamic Desirable       | Trunk                  |
| Dynamic Auto      | Trunk                   | Trunk                  |
| Dynamic Auto      | Access                  | Access                 |
| Dynamic Desirable | Dynamic Desirable       | Trunk                  |
| Dynamic Desirable | Trunk                   | Trunk                  |
| Dynamic Desirable | Access                  | Access                 |
| Trunk             | Trunk                   | Trunk                  |
| Trunk             | Access                  | Limited Connectivity    |
| Access            | Access                  | Access                 |

- **ملاحظات**:
  - لو الطرفين **Dynamic Auto**، المنفذين هيبقوا Access لأنهم بيستنوا بعض.
  - لو طرف **Dynamic Desirable** والتاني **Auto** أو **Desirable**، هيبقوا Trunk.
  - لو طرف **Trunk** والتاني **Access**، هتحصل مشكلة (Limited Connectivity) لأن الإعدادات مش متوافقة.



![[Pasted image 20250908211920.png]]

