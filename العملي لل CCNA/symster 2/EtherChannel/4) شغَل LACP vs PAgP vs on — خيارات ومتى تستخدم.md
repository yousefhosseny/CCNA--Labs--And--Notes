
- **LACP (IEEE 802.3ad)**: أوامر `mode active` / `mode passive`. لازم على الأقل طرف واحد يكون `active` لتتشكل القناة. (موصى به، متوافق بين بائعين).
    
- **PAgP (Cisco proprietary)**: `mode desirable` / `mode auto`. `desirable` نشط، `auto` سلبي — لازم طرف واحد `desirable`.
    
- **on** (force): مافيش تفاوض — لو رفعت `on` على جهة ومقابلها `on`، القناة هتتكوّن. لو استخدمت `on` مقابل `active` أو `passive` ممكن تحصل نتائج غير متوقعة. استخدمه فقط لو متأكد.
    
