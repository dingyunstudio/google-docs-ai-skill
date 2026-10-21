> 定沄整合設計工作室｜SOP01 公開衍生稿 0.1.0。
> [Skill 入口](../SKILL.md) · [章節總覽](../README.md#chapters) · [任務契約](../templates/task-contract.md) · [授權](../LICENSE)

# Google Docs AI Editing SOP｜公開衍生版

公開版 0.1.0｜衍生自定沄整合設計工作室 SOP01；本次公開封裝尚待獨立審查與完整實測。

*先驗證，再修改；先確認，再相信。*

適用：Google Docs 實際文件修改對話

## Execution Flow｜Execution AI Core Principle

Environment → CSV → Backup → Risk Classification → Verification Plan → Boundary Analysis → Structural Unit → Write → Immediate Readback → Verification → Structure Integrity → Evidence Preservation → Complete／Stop

任何一步失敗：立即進入 Verification Stop Rule → Escalation Threshold → Recovery／Planning Decision。不得跳步、不得以完成 Write 取代 Verification，也不得以 Readback 取代 Structure Integrity Check。

| **階段**           | **主要目的**                             | **對應章節／Rule** |
|--------------------|------------------------------------------|--------------------|
| 1\. Environment    | 確認工具、權限、Write／Readback 閉環     | 00、ED-CSV-01      |
| 2\. Trust Baseline | CSV＋Backup，建立安全起點                | 04.1、04.2         |
| 3\. Planning       | Risk、Verification、Boundary、Write Unit | 05、06、07         |
| 4\. Execution      | 逐 Unit Write 與 Immediate Readback      | 08.1、08.2         |
| 5\. Verification   | Paragraph／Neighbor／Sequence／Integrity | 08.3               |
| 6\. Evidence       | Request、Boundary、Revision、Readback    | 08.4               |
| 7\. Decision       | Complete 或 Stop／Escalate               | 09                 |

### Problem & Task Routing｜依問題精準選讀

| **我現在遇到／要做的事**        | **精確路徑**                                                        |
|---------------------------------|---------------------------------------------------------------------|
| 修改一句文字                    | 04.1 CSV → 05 Risk → 06 Verification → 08.1 Workflow → 14 Checklist |
| 修改一個 Paragraph              | 05 L2 → 06 V3 → 07.2 Structural Unit → 08.2 Readback                |
| 新增多段正文                    | 05 L3 → 06 V4 → 07.2 Structural Unit → 08.1 Workflow                |
| 新增 Heading／Guard             | 05 L4 → 06 V5 → 07.1 Boundary → 08.3 Integrity                      |
| 跨章節／Catalog／Guard Boundary | 05 L5 → 04.2 Backup → 07.1 Boundary → 08.2 L5 Scope → 08.4 Evidence |
| 不知道 L2／L4／L5               | 05.1 Write Risk Decision Tree                                       |
| 不知道要驗證到哪一層            | 06.1 Verification Decision Tree                                     |
| Readback 怪異                   | 08.2 Scope → 08.3 Integrity → 09.1 Stop Rule                        |
| Heading／下一章消失             | 09.1 Stop Rule → 09.3 Recovery Threshold                            |
| Connector 成功但未完成回讀      | GD-01／GD-09                                                        |
| 判斷是否可 Minimal Repair       | 07.3 Minimal Repair Boundary                                        |

### Rule Dependency Map

### Execution Dependencies｜輸入責任與操作規則分離

以下依賴鏈表示執行前提；箭頭不代表自動授權。必要輸入缺失、過時或未獲核准時，停在前一個可驗證節點。

私人框架的跨冊位置已適配為本套件的[任務契約](../templates/task-contract.md)與[證據報告](../templates/verification-report.md)。任務發布、授權與外部紀錄仍由使用者／任務負責人持有；本 Skill 只處理 Google Docs 修改 mechanics。

| 情境 | 必要依賴 |
|---|---|
| 新對話／接手 | 任務與有效授權 → Current／Last Known／Difference → 已知寫入與未驗證範圍 → Current Docs baseline |
| 一般 Write | 已核准 Task／Execution Plan → ED-CSV-01 → ED-RISK-01 → ED-VERIFY-01 → ED-UNIT-01 → ED-INTEGRITY-01 → ED-EVIDENCE-01 |
| Recovery | ED-STOP-01 → ED-REC-SOURCE-01 → Gate 1 Source／Plan 核准 → Gate 2 Recovery Write 核准 → ED-EVIDENCE-01 |
| Draft 正式發布 | Draft／Formal 身分分離 → 明確 Publishing／Write 授權 → ED-CSV-01 → 線上 Verification Evidence |
| 外部進度／Ledger | ED-EVIDENCE-01 → 可驗證停點／交付報告 → 外部負責人處理正式發布；不由本 Skill 自行改表 |

| **起點 Rule**   | **必須依賴**                   | **失敗時前往**            |
|-----------------|--------------------------------|---------------------------|
| ED-CSV-01       | ED-BACKUP-01／ED-RISK-01       | ED-STOP-01                |
| ED-RISK-01      | ED-VERIFY-01                   | 採較高 Level／回 Planning |
| ED-VERIFY-01    | ED-BOUNDARY-01／ED-READBACK-01 | ED-STOP-01                |
| ED-BOUNDARY-01  | ED-UNIT-01                     | ED-STOP-01                |
| ED-UNIT-01      | 08.1 Execution Workflow        | ED-STOP-01                |
| ED-READBACK-01  | ED-INTEGRITY-01                | ED-STOP-01                |
| ED-INTEGRITY-01 | ED-EVIDENCE-01                 | ED-ESCALATE-01            |

## Task Input Navigator｜獨立使用的輸入與責任

| 需求 | 輸入／閱讀入口 | 邊界 |
|---|---|---|
| 新 Task／Work Package | [任務契約：身分、授權與範圍](../templates/task-contract.md#task-identity) | AI 不得自行擴大或發布正式任務 |
| 修改 Google Docs | [準備](02-preparation-and-trust-baseline.md) → [執行](04-execution-and-verification.md) → [Checklist](06-operating-modes-and-checklists.md) | 只執行已核准範圍 |
| 新對話接手 | [Current baseline／continuity](../templates/task-contract.md#baseline) | 先查目前文件、最後寫入與未驗證範圍，再執行 |
| Recovery | [Source／Gate 輸入](../templates/task-contract.md#recovery)＋[Stop／Source Fitness](05-stop-escalation-and-guards.md) | Plan／Source 核准與 Write 核准分離 |
| Draft 正式發布 | [Route／Mode 與發布範圍](../templates/task-contract.md#route) | Draft 核准不等於 Write 核准 |
| 驗證新舊差異 | [證據報告](../templates/verification-report.md) | Current／Last Known／未驗證不得混用 |
| 外部 Ledger／正式欄位 | 使用者提供的已核准規格及外部處理方式 | 本 Skill 不定義或修改其 schema／正式狀態 |

## Quick Routing｜這次要讀哪些章節

本頁只提供選讀路徑，不取代正文規則。一般 Write 至少閱讀 00、02、04、05、06、07、09、14；高風險或章節邊界 Write 必須加讀 08、10 與 13。

| **需求／情境**              | **最短必讀路徑**                                                                                                                                                                         |
|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 一般文字／單句修改          | ED-CSV-01 → ED-RISK-01 → ED-VERIFY-01 → 08.1 Execution Workflow → 14 Checklist                                                                                                           |
| 段落／多段內容              | ED-UNIT-01 → ED-RISK-01 → ED-READBACK-01 → ED-EVIDENCE-01                                                                                                                                |
| Heading／章節／Catalog 邊界 | ED-BOUNDARY-01 → ED-INTEGRITY-01 → ED-STOP-01 → V5 Verification                                                                                                                          |
| Write 後出現異常            | ED-STOP-01 → ED-ESCALATE-01 → 09 Verification Stop／Escalation → 10 Google Docs Guard Catalog                                                                                            |
| Write 後工具中斷            | GD-09 → Evidence Record → Current State Re-read → 禁止重送                                                                                                                               |
| Google Docs 高風險修改      | 10 Google Docs Guard Catalog → ED-RISK-01 → ED-VERIFY-01 → ED-INTEGRITY-01                                                                                                               |
| 建立新長文件                | 12 Mode A｜Local DOCX First                                                                                                                                                              |
| 既有雲端文件修改            | 先讀 12.0.1 Route Comparison；依最新 Task／Owner／Planning boundary 選定合法 route 後再選 Mode。same-ID native route 適用時：小修→12 Mode B；大型／整章／多 Units／Render QA→12 Mode C。 |

## Core Rule ID Index

### Framework Rule Extensions

| **Rule ID**      | **正式名稱**                              | **用途**                                                                                                                                                                                                                                                     |
|------------------|-------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ED-BASELINE-01   | Current Baseline Consumption Rule         | 消化任務提供並經本輪確認的 Current Evidence                                                                                                                                                                                                                          |
| ED-REC-SOURCE-01 | Recovery Source Fitness Rule              | 評估來源適用性與限制                                                                                                                                                                                                                                         |
| ED-CANON-01      | Canonical Identifier Rule                 | 統一 Task／Rule／Status 正式名稱                                                                                                                                                                                                                             |
| ED-RULE-LIFE-01  | Rule Lifecycle Rule                       | Finding 至 Deprecated 的生命週期                                                                                                                                                                                                                             |
| ED-LEDGER-01     | Execution Verified-Stop Evidence Boundary | 進度／結果到可驗證停點且 Evidence 足夠後才可交付；本 Skill 只持有 Docs execution evidence／verified-stop mechanics。外部 Ledger／正式進度由使用者指定的負責人、現況與規格承接；Sheets mechanics 不在本 Skill 範圍。 |

| **Rule ID**     | **正式名稱**                  | **定義章節** | **適用**             |
|-----------------|-------------------------------|--------------|----------------------|
| ED-CSV-01       | Current State Verification    | 04.1         | 所有 Write           |
| ED-BACKUP-01    | Pre-Write Backup Gate         | 04.2         | 正式 Write／Recovery |
| ED-RISK-01      | Write Risk Classification     | 05           | 所有 Write           |
| ED-VERIFY-01    | Verification Depth            | 06           | 所有 Write           |
| ED-UNIT-01      | Minimum Structural Write Unit | 07.2         | L2～L5               |
| ED-BOUNDARY-01  | Structure Boundary Checklist  | 07.1         | L4～L5               |
| ED-READBACK-01  | Readback Scope Rule           | 08.2         | L1～L5               |
| ED-INTEGRITY-01 | Structure Integrity Check     | 08.3         | L3～L5               |
| ED-STOP-01      | Verification Stop Rule        | 09.1         | 所有異常             |
| ED-ESCALATE-01  | Recovery Escalation Threshold | 09.3         | Integrity 異常       |
| ED-EVIDENCE-01  | Evidence Preservation         | 08.4         | L4～L5 強制          |

| **核心原則｜Write Risk ≠ Request Count**                                                                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Write 的安全性，不應以 API request 的數量衡量，而應以修改所跨越的結構單元（Structural Units）與所需的驗證深度（Verification Depth）衡量。跨越章節、Heading 或 Guard Catalog 邊界時，即使只有一個 request，也應視為高風險 Write，拆分為最小 Structural Unit，逐步寫入、逐步回讀、逐步驗證。 |
