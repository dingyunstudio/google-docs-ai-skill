> 定沄整合設計工作室｜SOP01 公開衍生稿 0.1.0。
> [Skill 入口](../SKILL.md) · [章節總覽](../README.md#chapters) · [任務契約](../templates/task-contract.md) · [授權](../LICENSE)

**Part C｜Boundary & Structural Planning**  
適用：Boundary、Structural Unit、Minimal Repair 邊界與執行前拆解。

**07｜Boundary & Structural Planning**

**07.0｜Large Block vs Structural Unit Decision**  
可較大段一次寫入：新文件或全新空白 section、不插入既有結構中間、不跨 Heading／Catalog 邊界、內容來源完整、沒有後續既有內容需保護、可整體覆核、失敗可安全整段刪除或重建。

必須逐 Unit／逐段寫入：插入既有文件中間、前後都有需保護內容、新增 Heading、跨章節／Catalog、涉及 list／table／Guard sequence、Write 後 index 會改變、後續內容完整性屬 Acceptance、Recovery 困難或原文來源分散。

核心判定：長文字不必然高風險；在空白、隔離、可整體重建的環境中可較大段處理。嵌入既有重要結構時，即使文字不長，也必須逐 Structural Unit 寫入。

**07.1｜Structure Boundary Checklist【ED-BOUNDARY-01】**  
L4／L5 Write 前後都要使用同一份 Boundary Checklist。

□ 前方 Anchor／Heading 存在且內容正確。

□ Target Boundary 唯一。

□ 後方下一個 Heading／Section 存在。

□ 後續至少兩個結構單元存在且順序正確。

□ 沒有重複 Heading、重複 Guard 或意外 Merge。

□ 預期不修改的保護範圍已列出。

□ Write 後使用相同 Checklist 完整重驗。

**07.2｜Minimum Structural Write Unit【ED-UNIT-01】**  
安全單位是 Structural Unit，不是 API request。

• 一個 Heading 是一個 Unit。

• 一個 Paragraph 是一個 Unit。

• 一個 List Item／List Group 是獨立 Unit。

• Title、Risk、Correct Handling 不得塞進同一個長篇 insertText。

• 同一 request 包含多個 Structural Units 時，仍視為多個高風險修改，必須拆分。

**07.3｜Minimal Repair Boundary**  
Minimal Repair 只允許在全部條件同時成立時執行：Risk＝L1／L2；目標唯一；前後結構完整；沒有 Heading／下一章消失、Sequence Break、Unexpected Deletion、Paragraph Merge 或截斷；修正來源逐字明確；原 Write 與異常 Revision 可定位；且原 Task 明確授權局部修正。  
只要涉及 L4／L5 Boundary Integrity 異常、Heading／下一章消失、Paragraph 被合併到其他章節、後續內容截斷、受損範圍不明或原文來源不完整，必須立即 Stop → 保存 Evidence → 建立獨立 Recovery Task。不得先修看看。  
Localized Post-Write Correction 與 Minimal Repair 是不同模型。Minimal Repair 保留原本 L1／L2 bounded repair 邊界；Localized Post-Write Correction 則可適用於原 substantive Write 為 L3／L4／L5 的情況，但 Original Write Risk 不等於 Detected Anomaly Scope，不得因原 Write Risk＝L4／L5 就自動禁止所有局部 correction，也不得因 anomaly 看似 Style 就跳過 structure verification。  
Localized Post-Write Correction 只有在以下 Eligibility 全部成立時，才可在原 Task authorization boundary 內執行最多一次 bounded correction：Target 唯一；Immediate Readback 已證明 intended text 存在、唯一、完整且內容正確；Paragraph／Structural Unit boundary 正確；Neighbor／Sequence 正確；不存在 Heading loss、next section loss、Paragraph merge、sequence break、unexpected deletion、truncation、unknown inserted text 或 protected-scope change；anomaly scope 完全已知且局部；defect 僅限可局部、可逆、可明確驗證的 presentation／formatting defect，例如 wrong Named Style、paragraph style inheritance、text style inheritance、hyperlink style 或 equivalent bounded formatting defect；correct state 有明確可信來源，例如同文件 verified neighboring paragraph、clean pre-write baseline 或 authorized exact style requirement；correction 不增加新文字語意、不改 Task scope、不改 structure；且不需要新的 Planning decision、Recovery Source decision 或 authorization expansion。  
符合 Eligibility 時，只允許 one bounded correction attempt → Immediate Readback → Style／Paragraph／Neighbor／Sequence Verification。若 PASS，可繼續目前 Task Unit 後續已授權工作。若第一次 correction 後仍不符合 Expected State，立即 STOP；不得第二次試不同 repair method、逐步猜測 style、擴大修改範圍、重建 paragraph、用 backup wholesale replace 或切換 execution strategy。Automatic Disqualification：Heading／Section／Catalog structure 異常、Paragraph merge、sequence break、unexpected deletion、truncation、target／boundary ambiguous、anomaly scope unknown、source 不完整、intended text 本身不正確、write 未命中 target、connector result 與 readback 衝突且 state 不明、protected scope 被改、correction 需要 semantic rewrite、需要新增／刪除 Structural Unit，或會擴大 authorization scope。任一成立即不得使用 Localized Post-Write Correction，直接依既有 Stop／Recovery rules 處理。Localized Post-Write Correction 不得擴張成 L4／L5 general repair。

***Next Reading｜Boundary 與 Units 完成後，進入 08 Execution Workflow。***
