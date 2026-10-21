> 定沄整合設計工作室｜SOP01 公開衍生稿 0.1.0。
> [Skill 入口](../SKILL.md) · [章節總覽](../README.md#chapters) · [任務契約](../templates/task-contract.md) · [授權](../LICENSE)

# Part E｜Stop, Escalation & Guard Catalogs
適用：異常停止、Recovery 升級與 Google Docs Guard。

## 09｜Verification Stop、Escalation 與 Recovery Threshold

### 09.1｜Verification Stop Rule【ED-STOP-01】
只要出現下列任一情況，立即停止所有 Write；不得先修看看。

- Heading／下一章／Guard／重要結構單元消失。

- Structure Sequence 中斷或順序錯誤。

- Paragraph／Section 意外 Merge。

- Unexpected Deletion、截斷或大量內容遺失。

- 保護範圍被修改。

- Readback 與 Connector success／預期結果衝突。

- 必要 Evidence 或逐字來源不完整。

- 無法確認目前 Index／Boundary／Revision 是否仍有效。

例外僅限 07.3 已完整驗證 Eligibility 的 Localized Post-Write Correction：若 text、Paragraph boundary、Neighbor／Sequence 與 protected scope 均正確，且唯一 defect 為完全已知、可逆、可局部驗證的 presentation／formatting anomaly，可在原 Task authorization boundary 內執行一次 bounded correction。任何 structural anomaly 或一次 correction 後仍 FAIL，仍立即 STOP。

### 09.2｜Recovery Source Fitness Matrix【ED-REC-SOURCE-01】
Recovery Source 不依檔案類型自動排序，必須評估 Provenance、Completeness、Temporal Fit、Purpose Fit、Accessibility 與 Integrity。

所有待復原 Structural Unit 必須分別標記 Text Source、Format Source、Status 與限制。必要逐字來源未取得時，Recovery Plan 保持 BLOCKED，不得進 Gate 2。

| 來源角色 | 可做什麼 | 不可做什麼 |
| :---- | :---- | :---- |
| Current Formal Document／Current Revision | 確認損壞範圍、Boundary、未受影響區域 | 不可提供已遺失逐字原文 |
| Complete Prior Export／Approved Draft | 提供完整文字與順序 | 未比對前不可作格式權威 |
| Historical Revision（可能 PARTIAL） | 證明事故前結構、交叉驗證 | 截斷時不可作唯一逐字來源 |
| Pre-Recovery／Damaged-State Backup | 保存事故狀態、Rollback 基準 | 事故後備份不可冒充事故前原文 |
| Postmortem／Incident Report | 提供 Timeline、Root Cause、Detection Gap | 不是待復原文字來源 |
| Approved Task Text | 提供事故後新增規則的核准文字 | 缺少時 Gate 1 不得完成 |

### 09.3｜Recovery Escalation Threshold【ED-ESCALATE-01】
符合以下條件之一，原 Write Task 必須停止並另立 Recovery Task；不得繼續在原 Task 中試修。

- 任何 Heading、Section、Catalog 或重要文件結構損壞。

- 一次已授權的 Localized Post-Write Correction 後仍無法恢復 Expected State，或問題已升級為 Paragraph／Boundary／Sequence。

- 受損區域已包含未知來源文字或多個 Revision 的試修結果。

- 必要逐字來源只能 PARTIAL／UNKNOWN。

- 無法證明 Minimal Repair 不會擴大損害。

Recovery 的來源矩陣依本章 §09.2；[任務契約](../templates/task-contract.md#recovery)需附 Gate 1（Source／Plan 核准）與 Gate 2（Recovery Write 核准）的分別證據，以及目前損壞狀態、交接／接續資訊。Gate 1 不等於 Gate 2。缺少必要來源、核准或接續證據時不得開始 Recovery Write；實際 Write 仍須遵守本 SOP 的 Risk、Unit、Readback、Integrity 與 Evidence 規則。

***Guard Routing｜Google Docs Connector 與文件結構問題閱讀 10。***

## 10｜Google Docs Connector Guard Catalog

### 10.0｜Google Docs Structure Model
Google Docs Write 應以文件結構而非純文字索引理解。Structural Unit 包含 Paragraph、Heading、List Item、Table、Section、Catalog、Guard、Bookmark／Link、Revision Boundary。

| 結構單元 | 典型風險 | 最低驗證 |
| :---- | :---- | :---- |
| Paragraph | 樣式繼承、段落合併、句尾截斷 | V3＋Neighbor |
| Heading／Section | 下一章消失、層級漂移、Boundary 破壞 | L4／V5 |
| List／Catalog／Guard Sequence | 編號、順序、項目遺失或黏接 | 完整 Sequence Check |
| Table | 列欄移位、合併儲存格、標題列破壞 | 結構＋內容＋前後段 |
| Hyperlink／Bookmark | 顯示文字存在但 Link Target 錯誤 | 文字與關聯分開驗證 |
| Revision Boundary | CSV 後其他人修改、舊 index 落錯位置 | requiredRevisionId 或重新 Baseline |

### GD-01｜Connector 成功不是完成
問題現象／風險：occurrencesChanged、success 或新 Revision 只表示 API 接受請求。

正確處理：立即回讀並完成要求的 Verification。

### GD-02｜每個 Write Unit 立即回讀
問題現象／風險：累積多個修改後才檢查，會失去錯誤來源。

正確處理：一個 Structural Unit 對應一次立即回讀。

### GD-03｜短句不是唯一標準
問題現象／風險：短文字通常較安全，但短 request 仍可能跨結構邊界。

正確處理：同時檢查文字長度與 Structural Units。

### GD-04｜唯一性確認
問題現象／風險：相同文字可能出現多次。

正確處理：replaceAllText 前確認唯一；否則使用 Anchor／Boundary／精確 index。

### GD-05｜樣式確認
問題現象／風險：新增文字可能繼承 Heading、List 或錯誤 Text Style。

正確處理：Paragraph Style、Text Style、Hyperlink 分開驗證。若 Immediate Readback 證明 structure integrity 正常、唯一 defect 為符合 07.3 Eligibility 的 bounded style anomaly，可依 Localized Post-Write Correction 執行一次 correction；否則走 Stop／Recovery。

### GD-06｜Revision mismatch
問題現象／風險：requiredRevisionId 過期時，舊定位與版本可能失效。

正確處理：重新讀取最新 Revision，不盲目重送。

### GD-07｜前後段與結構確認
問題現象／風險：新句正確不代表段落或下一章仍正確。

正確處理：依 Risk Level 執行 Neighbor／Sequence Check。

### GD-08｜跨 Task 重新驗證
問題現象／風險：前一 Task 正常不代表下一 Task 開始時仍正常。

正確處理：每個新 Write Task 重新 CSV。

### GD-09｜Write 後回讀中斷復原
問題現象／風險：Write 已送出，但回讀完成前 Connector、權限或環境中斷。

正確處理：不得宣告完成或重送。記錄 request／Target／Revision，標記 WRITTEN\_UNVERIFIED；工具恢復後先重新回讀目前文件，確認 Write 是否存在、唯一且完整，再決定驗證、Minimal Repair 或 Recovery。

### GD-10｜Named Style 不等於實際正文格式
問題現象／風險：NORMAL\_TEXT 或 Named Style 可能與文件內實際正文外觀不同。

正確處理：以同文件內已驗證的正常段落作格式基準；Paragraph Style、Text Style、Hyperlink 分開處理並逐步回讀。
