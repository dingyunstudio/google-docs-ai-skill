> 定沄整合設計工作室｜SOP01 公開衍生稿 0.1.0。
> [Skill 入口](../SKILL.md) · [章節總覽](../README.md#chapters) · [任務契約](../templates/task-contract.md) · [授權](../LICENSE)

# 15｜Guard Log、Maintenance 與文件拆分

## 15.1｜Rule Lifecycle【ED-RULE-LIFE-01】

## 15.2｜Concept-to-Rule Mapping Registry
所有成熟概念都必須有明確落點。若一個概念已被既有 Rule 吸收，不應再用新名稱重複建立；若仍有缺口，應產出 Mapping Finding，而不是直接擴寫正文。

| 概念 | 主要落點 | Rule Reuse 判定 | 剩餘缺口 |
| :---- | :---- | :---- | :---- |
| Minimum Structural Write | ED-UNIT-01／ED-BOUNDARY-01 | CONSOLIDATION | 無；持續用案例驗證 |
| Draft First | 任務契約的 Draft／Formal 與 Publishing 範圍 | CONSOLIDATION | 本 Skill 只消費已核准範圍 |
|  |  | CLARIFICATION | 需要第二次可重現證據才升正式 Guard |
| Recovery Approval Gate | 任務契約的 Gate 1／Gate 2 證據 | DUPLICATE／REFERENCE | 本 Skill 只處理 Gate 2 後的 Write 安全 |
| Current Evidence Comparison | 任務契約的 Current／Last Known／Difference | CONSOLIDATION | 本 Skill 消化輸出；使用者管理任務 |
| Current vs Historical Authorization | 目前核准任務的 authorization authority | NEW\_RULE／CLARIFICATION | 本 Skill 只消費 Current authorization；外部 facts／semantics 由負責人提供 |
| Canonical Task／Rule／Status／Evidence | ED-CANON-01＋目前核准任務的 authority | NEW\_RULE | 本 Skill 不定義外部 dictionary／value domain |
| Publication Lifecycle | ED-LEDGER-01 evidence boundary＋證據報告＋使用者正式發布責任 | NEW\_RULE | 本 Skill 不擁有外部 publication lifecycle |
| Evidence Lifecycle／Mapping | §08.4.1＋任務契約／證據報告 | NEW\_RULE | 外部 evidence semantics 由負責人提供；本 Skill 保留 execution evidence mapping |

Rule Lifecycle：Finding → Rule Reuse Check → Planning Draft → Approved Write Task → Published Rule → Verified in Use → Deprecated／Superseded。

Rule Reuse Check 固定結果：NEW\_RULE、CLARIFICATION、CONSOLIDATION、DUPLICATE、CONFLICT。Execution AI 負責發現與證據；Planning AI 負責制度化決策。

- 新踩雷先記錄 Finding／Guard Log；重複出現或可泛化後再升級正式 Rule。

- 同一規則只在正文定義一次；Checklist、Template 與 Anti-pattern 優先引用 Rule ID。

- 文件超過 40～45 頁、Rule 重複超過三處、導航失效或 Connector 經常截斷關鍵後段時，啟動 Read-only Consolidation Review。

- Execution AI 不得自行拆分 SOP；先做 Rule Mapping、提出整理計畫、等待使用者核准。

# 16｜與任務契約及外部工作的關係

## 16.1｜Related Reading by Need

### 16.1.1｜Exact Related Reading Baseline

本套件不要求私人手冊、中央 Ledger 或特定資料夾。必要 Current baseline、任務身分、授權、Recovery 及外部依賴由使用者／任務負責人提供可查證輸入；本 Skill 不擴張其責任。

| 主題 | 公開入口 | 輸入／責任 |
|---|---|---|
| Current Baseline／接續 | [任務契約](../templates/task-contract.md#baseline) | Current／Last Known／Difference、最後 Write／Readback、未驗證範圍 |
| Draft／Formal | [任務契約](../templates/task-contract.md#route) | 明確 Formal target 與 Publishing／Write 授權 |
| Recovery | [Source／Gate](../templates/task-contract.md#recovery)＋[§09](05-stop-escalation-and-guards.md) | Source／Plan 核准與 Write 核准分離；來源不足保持 BLOCKED |
| 進度／外部紀錄 | [證據報告](../templates/verification-report.md) | 可驗證停點與 Evidence 交給外部負責人；不自動改表 |
| Rule Reuse／維護 | 本章 §15、[唯讀審查報告](../templates/verification-report.md#review) | 先 Finding／Mapping，後使用者決策 |

## 16.2｜Verification Review Contract｜新對話只論證、不修改

## 16.3｜Framework Verification Acceptance & Stop Rule
Verification Review 只有在下列成果全部具備時才算完成；任何一項缺失，Status 只能是 READ\_ONLY\_FINDING／BLOCKED／WAITING\_APPROVAL，不得宣告 Framework 已通過。

完成後必須停止，等待使用者／Planning AI 發布後續 Publishing、Recovery、 或 Maintenance Task。不得在同一 Review 中直接修正。

| 驗收項目 | 通過條件 |
| :---- | :---- |
| Navigation | 每個高頻需求都能在兩次跳轉內抵達主責章節、Rule ID 與 Stop Condition |
| Dependency | Rule／Task／Evidence／Schema 依賴鏈完整，且不把引用當授權 |
| Canonical Naming | Task、Rule、Status、Evidence 無未說明別名或衝突 |
| Task Mapping | 已完成、未發布、被 Draft 吸收、需重新授權與應關閉項目均可辨識 |
| Rule Reuse | 所有候選概念已有 NEW／CLARIFICATION／CONSOLIDATION／DUPLICATE／CONFLICT 判定 |
| Schema（審查範圍適用時） | 已提供的 Dictionary、Dropdown、Validation、Dashboard 與核准規格一致；外部實際修改另立任務 |
| Evidence | 重要結論都有 Current Evidence 或明確標記 Last Known／UNVERIFIABLE |
| Publication | Draft、正式發布、已驗證、已取代的轉換與證據完整；正式欄位值依已核准任務 |

當新對話的任務是驗證 Framework 是否落實時，Deliverable Mode 必須為 READ\_ONLY\_REVIEW。不得直接修正文件、Ledger、Rule ID 或狀態。

Verification Review 完成後停止，等待 Planning AI／使用者決定後續 Publishing、Recovery、 或 Maintenance Task。

| 必交成果 | 最低內容 |
| :---- | :---- |
| Evidence | 實際讀取的文件、Revision、Range、時間與限制 |
| Difference Report | Formal／Draft／Last Known／Current 的差異 |
| Gap List | 缺失規則、缺失欄位、缺失證據與缺失 Task |
| Conflict | 規則、章節、狀態、授權或來源互相矛盾 |
| Navigation Failure | 需求無法透過 Routing／Index 抵達正確規則 |
| Naming Conflict | Canonical Task／Rule／Status／Evidence 名稱不一致 |
|  |  |
| Task Mapping | 已完成、未發布、被 Draft 吸收、需重新授權或應關閉 |
| Rule Reuse | NEW\_RULE／CLARIFICATION／CONSOLIDATION／DUPLICATE／CONFLICT |
| Improvement Proposal | 只提方案與依據；不直接修改 |

| 需求 | 本 Skill | 使用者／任務負責人 |
|---|---|---|
| 一般正式 Write | Risk／Unit／Verification／Checklist | Task Contract、Authorization、正式進度處理 |
| Recovery | Stop／Source Fitness／Recovery Write Safety | Source／Plan 核准、獨立 Write 核准、Recovery Task 範圍 |
| Draft 正式發布 | 實際 Google Docs Write 安全 | Publishing Authorization 與正式身分／cutover 決策 |
| 新對話驗證缺失 | 只讀 Rule／Navigation | Current baseline、任務對照、後續改動決策 |

**Navigation Index｜我要找什麼**

| 問題／關鍵字 | 跳轉位置 |
| :---- | :---- |
| CSV／目前文件信任 | 04.1｜ED-CSV-01 |
| 備份／BACKUP\_VERIFIED | 04.2｜ED-BACKUP-01 |
| L0～L5 | 05｜ED-RISK-01 |
| V1～V5 | 06｜ED-VERIFY-01 |
| Heading／章節邊界 | 07.1｜ED-BOUNDARY-01 |
| Write Unit | 07.2｜ED-UNIT-01 |
| Minimal Repair | 07.3 |
| Write／Immediate Readback | 08.1 |
| Readback 看多少 | 08.2｜ED-READBACK-01 |
| Structure Integrity | 08.3｜ED-INTEGRITY-01 |
| Evidence／Revision | 08.4｜ED-EVIDENCE-01 |
| 停止／不得先修 | 09.1｜ED-STOP-01 |
| 轉 Recovery | 09.3｜ED-ESCALATE-01 |
| Docs Connector | 10 |
| Google Docs | 10 |
| 完成 Checklist | 14 |

**Case Study Boundary｜事故案例只作證據**

事故 Timeline、Root Cause、Detection Gap 與 Recovery Source 保存於 Postmortem／Finding／Evidence；正文規則使用可泛化模型，不以歷史事故任務名稱作永久流程條款。新 Task 不得因舊案例存在，就沿用其 Revision、Source Priority 或 Stop Point。私人歷史任務的驗證清單不屬於本公開套件的現行待辦。
