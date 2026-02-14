
## 7) نصايح عملية / checklist للتطبيق الآمن (مختصر وسهل التطبيق)

1. حدّد topology واضح: مين uplinks، مين access ports، مين hypervisors.
    
2. **فعّل PortFast** على جميع Access ports فقط: `spanning-tree portfast` أو `spanning-tree portfast default` بعد التأكد. ([Cisco](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9500/software/release/17-1/configuration_guide/lyr2/b_171_lyr2_9500_cg/b_171_lyr2_9500_cg_chapter_0101.pdf?utm_source=chatgpt.com "Configuring Optional Spanning-Tree Features"))
    
3. **فعّل BPDU Guard** على portfast ports (global أو per-interface). هذا يعطّل أي محاولة إدخال سويتش على access port فوراً. ([Cisco](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9200/software/release/16-12/configuration_guide/lyr2/b_1612_lyr2_9200_cg/configuring_optional_spanning_tree_features.html?utm_source=chatgpt.com "Layer 2 Configuration Guide, Cisco IOS XE Gibraltar 16.12. ..."))
    
4. استخدم **BPDU Filter** فقط لحالات خاصة وبعد اختبار — لا تفعلها على روابط بين سويتشات. ([Cisco](https://www.cisco.com/en/US/docs/switches/metro/me3600x_3800x/trash/swstpopt.html?utm_source=chatgpt.com "Configuring Optional Spanning-Tree Features [Support]"))
    
5. فعّل **Root Guard** على المنافذ التي لا تريد أن تصبح مصدر الجذور منها (uplinks غير مصممة لتكون root). ([Cisco](https://www.cisco.com/c/en/us/support/docs/lan-switching/spanning-tree-protocol/10588-74.html?utm_source=chatgpt.com "Enhance STP with Root Guard"))
    
6. فعّل **Loop Guard** على روابط بين السويتشات (non-portfast) لمنع التحول العشوائي إلى forwarding. ([Cisco](https://www.cisco.com/c/en/us/support/docs/lan-switching/spanning-tree-protocol-stp-8021d/218321-configure-stp-with-loop-guard-and-bpdu-s.html?utm_source=chatgpt.com "Understand STP Loop Guard and UDLD Features"))
    
7. فعّل **UDLD (aggressive)** على الألياف أو وصلات حساسة لاكتشاف unidirectional links. ([Cisco](https://www.cisco.com/c/en/us/support/docs/lan-switching/unidirectional-link-detection-udld/217977-configure-the-udld-protocol-feature.html?utm_source=chatgpt.com "Configure the UDLD Protocol Feature - Cisco"))
    
8. لا تفعل `errdisable recovery` لكل الحالات بدون مراجعة: لو فعلت `errdisable recovery cause bpduguard` مع `errdisable recovery interval`، افهم إن هذا يسمح بإعادة فتح المنفذ تلقائياً — مفيد للحوادث العرضية، لكن قد يُخفي هجمات متكررة. ([Cisco](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9300/software/release/17-8/command_reference/b_178_9300_cr/interface_and_hardware_commands.html?utm_source=chatgpt.com "Command Reference, Cisco IOS XE Cupertino 17.8.x ..."))
    
9. راقب دائماً: `show interfaces status err-disabled`، `show errdisable recovery`، `show logging`، وSNMP/syslog alerts.
    

---
