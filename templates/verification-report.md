# Google Docs 驗證與交付報告

> 依 SOP01 §01 Mandatory Report、§06、§08、§09 與 GD-09 整理。
> 每個重要結論附可查證證據。未取得、未讀回或未支援的項目寫 UNVERIFIABLE／限制；不以勾選代替查證。

## 1. Core Report

| 欄位 | 實際結果 |
|---|---|
| Task／Work Package | |
| Task Type | |
| Task Status | |
| Authorization Status／本次使用的核准證據 | |
| Authorization Boundary | |
| Current Execution Status | |
| Execution Phase | |
| Write Risk Level | |
| Required／Actual Verification Level | |
| Verification Coverage／Confidence | |
| Document ID／URL／Title／MIME／Parent／Tab | |
| Write Unit／Target Boundary | |
| Readback Scope | |
| Backup ID／URL／Role／Status／最終位置 | |
| Before Revision／After Revision | |
| Source／Candidate／Backup Hash（適用時） | |
| Verification Evidence／保存位置 | |
| Stop Point | |
| 未驗證／未完成／需決策事項 | |

## 2. CSV 與 Pre-Write Gate

逐項附證據或 N/A 理由：

- 本輪 Current 文件完整性、前次停點與修改、目前 Revision、唯一目標。
- 前後段、Heading、下一章、必要 Guard／Exception、未解衝突。
- 已核准的 Execution Plan、適用 Backup Gate、Risk／Verification、Structural Units。
- Target／Protected Scope、適用的 Boundary Checklist。
- Runtime 的 Write→Immediate Readback→Verification 能力；修正能力僅限 §07.3 對應 Eligibility。

## 3. 每個 Unit 的 Write／Readback／Verification

| Unit | Action／Request Evidence | Target／Before Revision | 預期改動 | 實際回讀／After Revision／時間 | V-Level／範圍與證據 | 結果／限制 |
|---|---|---|---|---|---|---|
| | | | | | | |

保存原 request 與原生 write-control 證據；需要時指出 matched occurrences 與最終 Target 唯一性的依據。每個 Unit 通過要求的驗證後才處理下一 Unit。

若讀回中斷，記錄最後已送出的 request、位置、Revision 與已知結果，標示 WRITTEN_UNVERIFIED。工具恢復後先回讀 current；不要猜測或重送。

## 4. Integrity、Style 與版面

| 檢查 | 已覆蓋區域／證據 | 結果／未覆蓋限制 |
|---|---|---|
| Intended text 完整、唯一、內容正確 | | |
| Paragraph／List／Table Units | | |
| Heading／Section／Guard Sequence | | |
| 前後 Anchor／下一章／後續 Units | | |
| Missing／Duplicate／Merge／Unexpected Deletion | | |
| Protected Scope | | |
| Paragraph Style／Text Style／Named Style | | |
| Hyperlink／Bookmark target | | |
| Render／Visual QA（適用時） | | |
| metadata／正式身分／URL／parent（適用時） | | |

只拿到純文字時不能宣稱完成樣式、結構或版面驗證。合理 index 位移與內容損壞應按來源、邊界及預期差異分辨。

## 5. Minimal Repair／Localized Correction（如適用）

| 欄位 | 證據與結果 |
|---|---|
| 使用哪種模型／對應 §07.3 條件 | |
| 原 Task authorization／Original Write Risk | |
| Target、內容、Boundary、Neighbor／Sequence、Protected Scope 驗證 | |
| anomaly scope、正確來源、全部 Eligibility／失格條件判定 | |
| 已使用的 correction attempt 次數 | |
| correction request／Immediate Readback／驗證 | |
| 是否達 Expected State／是否停止 | |

兩種模型不能合併為 retry loop；符合 Localized Post-Write Correction 才能執行一次 bounded formatting correction。一次仍 FAIL 或結構不完整，停止並依 Recovery 邊界處理。

## 6. Issue & Escalation Report（異常時）

- 發現異常、首次時間／Revision：
- 觸發的 Stop Rule／是否停止所有 Write：
- Task Status／Current Execution Status（分欄）：
- 受影響與未知範圍：
- 已保留 Evidence／Damaged-State Backup：
- 已知 request／最後 Write／最後 Readback／Do Not Redo：
- 既有 Guard／Rule：
- Recovery Source 狀態／限制；Gate 1／Gate 2 證據：
- 建議的獨立 Recovery Task／待使用者決策：
- 目前 Stop Point／安全接續前需先查證的事：

<a id="review"></a>
## 7. Framework 唯讀 Review（任務適用時）

依 §16 僅論證、不修改；以核准的審查範圍判定 N/A，不拿其他框架的 schema／狀態當本任務規格。

| 必交成果 | 本次證據／發現 |
|---|---|
| 實際讀取來源、版本／Revision、範圍、時間與限制 | |
| Current／Last Known／Formal／Draft Difference | |
| Gap List／Conflict | |
| Navigation Failure／Naming Conflict | |
| Task Mapping | |
| Rule Reuse：NEW_RULE／CLARIFICATION／CONSOLIDATION／DUPLICATE／CONFLICT | |
| Improvement Proposal；未直接修改 | |

完成 Review 後停在可驗證停點，後續 Publishing、Recovery 或 Maintenance 由使用者／任務負責人決定。

## 8. 最終交付

逐項對 Acceptance 說明已驗證結果與限制。只有要求的 Verification／Integrity 全部通過且必要證據完整，才宣告 VERIFIED_COMPLETE；API success 或部分檢查通過不作替代。

- 已完成且有證據：
- 尚未寫入／未驗證／BLOCKED：
- 外部負責人需承接的進度／紀錄：
- 下一個必要動作與本次 Stop Point：

© 2026 定沄整合設計工作室｜[CC BY-NC-SA 4.0](../LICENSES/CC-BY-NC-SA-4.0.txt)
