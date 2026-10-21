> 定沄整合設計工作室｜SOP01 公開衍生稿 0.1.0。
> [Skill 入口](../SKILL.md) · [章節總覽](../README.md#chapters) · [任務契約](../templates/task-contract.md) · [授權](../LICENSE)

**Part B｜Preparation & Trust Baseline**  
適用：CSV、Backup、Write Risk、Verification Planning 與修改前信任建立。

**04｜Pre-Write Control Gates**  
閱讀順序：04.1 Current State Verification → 04.2 Backup Gate → 04.3 Revision Write Control。章節號代表執行順序；不得因版面位置跳步。

**04.1｜Current State Verification【ED-CSV-01】**  
• 文件完整性：未異常截斷、未大量遺失、未出現未知同步或格式異常。

• 停點：上一個 Task 真正停點與未驗證項目。

• 前次修改：內容仍存在且格式正常。

• 目標：位置、文字、Boundary 或 Anchor 唯一。

• 版本：目前 Docs／Drive Revision 可安全使用。

• 必要上下文：前後段、Heading、下一章、後續 Guard、Exception 與 Anti-pattern。

**04.2｜Pre-Write Backup Gate【ED-BACKUP-01】**

**04.3｜Revision Write Control**  
正式 L4／L5 Write 若 Connector 支援 requiredRevisionId，必須使用最新回讀取得的 revision ID。若 requiredRevisionId 不再匹配，Write 必須失敗並重新執行 CSV、Boundary 定位與 Risk／Verification 判定；不得自動 merge 或沿用舊 index。

Backup 適用基準：L0／L1 可依 Task 判定；L2 涉及正式關鍵文字時需要；L3 原則上需要；L4、L5 與任何 Recovery Write 強制建立並驗證 Backup。

每個 Work Package 第一次修改某份正式文件前，必須建立並驗證修改前 Backup Copy。新的高風險 Task、基準已改變或前一備份不再代表目前文件時，必須重新備份。

• 正式／最終保留的 Backup Copy 必須存放於 使用者指定且已驗證的 Google Drive 備份資料夾；本機或工作區備份只能作暫存，不得作唯一長期來源。

• 工作區匯出檔只能作第二層臨時備份，不得作唯一長期來源。

• 記錄原文件名稱／連結、Backup Copy ID／連結、建立時間、WP ID、Task ID、Docs Revision、Drive Revision、Backup Role 與 Backup Status。

• Backup Copy 可開啟並可存取後，才標記 BACKUP\_VERIFIED。

• 備份失敗、權限不足、無法驗證或資料夾不存在時，Current Execution Status＝BLOCKED，禁止 Write。

• Google Docs Version History 是輔助，不取代明確 Backup Copy。

**05｜Write Risk Classification【ED-RISK-01】**

**05.1｜Write Risk Decision Tree**  
無法確定 L3／L4／L5 時，一律採較高風險等級；不得為了降低流程成本而向下分類。

只改 Metadata／Comment／Tag？→ L0。只改唯一短文字？→ L1。改一個 Paragraph？→ L2。改多個 Paragraph／Units、但不跨 Heading／Section？→ L3。新增或修改 Heading／List／Section Header？→ 至少 L4。跨章節、Catalog、Guard 或其他重要 Structure Boundary？→ L5。多項同時成立時採最高 Level。

Write Risk 由修改目標的結構複雜度決定，不由 request 數量決定。

| Level | 定義 | 最低 Verification | 風險 |
| :---- | :---- | :---- | :---- |
| L0 | Metadata／Comment／Tag 等非正文內容 | 輕量 V1；仍需確認結果 | 低 |
| L1 | 單一文字或唯一短句 | V1；涉及格式時 V2 | 低 |
| L2 | 單一 Paragraph | V3 | 中 |
| L3 | 多個 Paragraph／Units，但不跨主要邊界 | V4 | 中高 |
| L4 | 新增／修改 Heading、List、Section Header 或重要格式邊界 | V5 | 高 |
| L5 | 跨章節、Catalog、Guard 或其他重要 Structure Boundary | V5＋Backup＋Evidence＋Sequence Check | 最高 |

 

判定原則：若同時符合多個 Level，採最高風險。無法判定時不得向下估計，先標記較高 Level 或回 Planning AI。

***Next Reading｜完成 Risk 判定後，閱讀 06 Verification Depth；L4／L5 再進 07.1 Boundary Checklist。***

**06｜Verification Depth【ED-VERIFY-01】**

**06.0｜Verification Framework：Depth、Coverage、Confidence**  
Verification 不能只回答『有沒有回讀』。必須同時記錄 Depth、Coverage 與 Confidence；三者任一不足時，不得宣告 VERIFIED\_COMPLETE。

無法確定 Coverage 是否足夠時，應擴大 Read-only 驗證範圍或回 Planning；不得以『看起來正常』補足缺失證據。

| 維度 | 定義 | 最低要求 |
| :---- | :---- | :---- |
| Verification Depth | V1-V5：從值存在到完整結構序列 | 依最高 Write Risk 對應 |
| Verification Coverage | 實際檢查了哪些 Unit、Boundary、上下游與未受影響區 | L4／L5 必須涵蓋完整保護範圍 |
| Verification Confidence | HIGH／MEDIUM／LOW，依證據完整度與可重現性判定 | 正式完成原則上需 HIGH；MEDIUM 必須說明限制 |
| Boundary Ownership | 誰負責證明前後 Anchor、受保護內容與跨文件依賴 | Task Contract 必須指定；不得留給工具自行推斷 |

**06.1｜Verification Decision Tree**  
無法確定 V4／V5 時，一律採 V5；Verification Level 只能向上提高，不得為了快速完成而降低。

只需確認文字存在？→ V1。涉及格式？→ 至少 V2。涉及完整 Paragraph？→ 至少 V3。涉及多 Units 或相鄰 Boundary？→ 至少 V4。涉及 Heading、Section、Catalog、Guard Boundary 或任何 L4／L5 Write？→ 強制 V5。

| Level | 驗證層級 | 最低內容 |
| :---- | :---- | :---- |
| V1 | Text | 文字存在、唯一且完整 |
| V2 | Style／Format | 字型、Named Style、格式、連結、數字格式 |
| V3 | Paragraph Unit | 段落或列表單元完整 |
| V4 | Neighbor／Boundary | 前後段、相鄰 Unit、Boundary 未黏合或位移 |
| V5 | Structure Sequence／Integrity | 完整 Heading／Section／Guard 序列、缺漏、重複、Merge、Unexpected Deletion |

 

Verification Level 是最低要求，不是上限。L4／L5 強制 V5；Connector success、Revision 變更或 occurrencesChanged 不能取代任何 Verification。

***Next Reading｜完成 Verification Plan 後，進入 07 Boundary & Structural Planning。***
