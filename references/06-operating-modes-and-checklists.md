> 定沄整合設計工作室｜SOP01 公開衍生稿 0.1.0。
> [Skill 入口](../SKILL.md) · [章節總覽](../README.md#chapters) · [任務契約](../templates/task-contract.md) · [授權](../LICENSE)

## 12｜Google Docs Operating Modes

### 12.0｜Mode Selection

**Mode A：建立大型全新文件，先本機完成整體內容與版面，再以正式 Import／Publishing 流程建立新文件。**

**Mode B：既有雲端文件的小範圍、唯一 Target、少量 Structural Units 修改，直接使用原生 Google Docs Write＋Immediate Readback。**

**Mode C：既有雲端文件的大型／整章／多 Units 修改，或需要完整 Render／Visual QA 時，先以 Local DOCX 作編輯與 QA 暫存，再把差異轉成受控 Native Patch 回寫原 Document ID。**

**選擇 Mode 不以「頁數」作唯一標準；頁數只能作提示。主要依修改跨越的 Structural Units、Boundary Risk、視覺 QA 需求與 Recovery 成本判斷。同一任務開始正式 Write 後，除非使用者另行授權，不得因某一路徑失敗而自行切換寫入策略。**

#### 12.0.1｜Route Comparison Before Mode Selection

**先 route、後 mode。Mode A／B／C 是 Google Docs mechanics model，不是 File ID、canonical link、custody、publication identity 或 cutover authorization；01 只執行 Docs HOW，不自行創造這些 substantive outcome／route consequence。**

**先 fresh-read 最新 Formal Task／Owner／Planning boundary，只比較該 boundary 內合法的 route candidates。候選可包含 bounded native patch、structured／batch native patch、local candidate＋controlled native patch、new-file import＋cutover，以及其他 runtime-proven 且 Task-authorized route。**

**Route comparison 至少評估 structural complexity、candidate／render readiness、File ID／canonical link／custody／inbound dependencies、recovery／destructive risk、online verification，以及目前 runtime／capability。**

**若 route 會改變 File ID、canonical link、authority／custody、parent location、recovery model、publication identity 等 substantive consequence，而最新 Task／Owner／Planning boundary 未明確授權，立即 STOP，回 Planning／Owner；不得靠 Mode Selection 自行決定。**

**最新 Task／Owner／Planning boundary 優先於本章 mechanics default：NEW\_FILE\_CUTOVER\_ALLOWED 不得因 Mode C 被硬化為 same-ID；SAME\_ID\_REQUIRED 也不得因 cutover 較方便而被覆寫。完成 route comparison 後，才使用 A／B／C 選擇該已授權 route 的 Docs 操作方式。**

### 12.1｜Mode A：大型新文件建立  
1. 先在本地建立完整 DOCX。

2. 完成內容、結構與版面 QA。

3. 由使用者上傳或以正式 Import Task 發布。

4. Connector 只負責後續小幅維護。

### 12.2｜Mode B：既有雲端文件維護  
1. CSV。

2. Backup Gate。

3. Risk／Verification 判定。

4. 定位單一 Target／Boundary。

5. 逐 Unit Write。

6. 立即 Readback。

7. Verification／Integrity。

8. 保存 Evidence。

9. 下一 Task 前重新 CSV。

### 12.3｜Mode C：大型既有文件｜Local DOCX Staging + Controlled Native Patch

**適用前提：本節描述的是 same-ID／original-Document-ID controlled native patch mechanics。只有 fresh-read 後的 Formal Task／Owner／Planning boundary 允許或要求此 route 時才套用；若 Task 已授權／要求 new-file cutover 或其他 compliant route，不得僅因「大型既有文件」而以 Mode C 把它改寫成 same-ID requirement。先依 12.0.1 完成 route comparison。**

**適用：既有 Google Docs 需要整章、多段、大量 Structural Units、批次內容重整，或必須先完成完整 Render／Visual QA，直接在雲端逐步編輯會增加施工與視覺驗證成本時。**

**核心原則：本機 DOCX Candidate 是「編輯與 QA 暫存面」，不是預設的原生 Google Docs 整份覆蓋傳輸格式。正式回寫仍以目前 Connector 對原生 Google Docs 明確支援的 native write 能力為準。**

**目前 Connector 契約邊界：一般 Drive 檔案的 raw-byte update action 搭配 file\_uri 用於一般 Drive 檔案的 raw bytes replacement；原生 Google Docs／Sheets／Slides 的內容修改應使用各自的專用 batch-update action。file\_uri 也必須是 Connector／Runtime 產生的檔案參照，不得把一般本機絕對路徑字串直接當成已成立的 upload contract。過去某個 Runtime 曾成功，不代表目前環境可直接沿用。**

**除非目前 Runtime 明確提供、實際驗證且使用者另外授權「保留原生 Google Docs 身分的整份原地替換能力」，否則不得把 update\_file＋DOCX bytes 當成 Mode C 的預設正式回寫方式。**

**Mode C 固定流程：**

**1\. Ground 原 Google Docs：確認 Document ID、Title、Parent、MIME、URL、modifiedTime、Tabs／Section／Table 等必要結構與最新 Revision。**

**2\. Pre-Write Backup：先建立可驗證的 Backup Copy；正式／最終保留的 Backup Copy 必須歸檔到 使用者指定且已驗證的 Google Drive 備份資料夾。**

**3\. Export：將目前原生 Google Docs 匯出為 DOCX，作為本機編輯基準。**

**4\. Local Baseline：必要時建立本機 Source Backup，計算 Source／Backup SHA-256；Hash 不一致不得開始 Candidate 修改。**

**5\. Candidate：由已驗證 Source DOCX 建立獨立 Candidate，只修改授權範圍，不直接改本機 Source Backup。**

**6\. Local Content QA：確認目標內容、原始正文、Heading／Section／Table／Hyperlink／Paragraph 順序與 Protected Scope。**

**7\. Render QA：將 Candidate 轉 PDF／頁面影像，檢查頁數、裁切、破版、表格溢出、頁首頁尾、中文字型、異常空白頁與其他視覺問題；需要 Layout-sensitive QA 時必須 PASS。**

**8\. Structured Diff：把 Candidate 與 Source 的差異轉成可執行的 Target／Anchor／Insert／Delete／Replace／Protected Scope 清單；Candidate 本身不得直接被當成雲端 Write 授權。**

**9\. Re-Ground：正式回寫前重新讀取原 Google Docs 最新 Revision 與目標 Boundary；若自 Export 後已有他人修改或 Boundary 漂移，停止並重做 Difference／Merge Planning，不得用舊 Candidate 覆蓋新內容。**

**10\. Native Patch：以目前 Runtime 明確支援的原生 Google Docs batch-update action 對原 Document ID 進行受控修改；依 Structural Unit 拆分，優先使用精確文字／Anchor／Boundary 與 requiredRevisionId，不做整份盲目重建。**

**11\. Immediate Readback：每個 Write Unit 後立即回讀，完成對應 Verification Level；任一 Unit 不符預期立即 Stop，不得繼續下一批。**

**12\. Final Integrity：全部 Write 完成後，確認 Heading／Paragraph／Sequence／Boundary／Table／Link／Unexpected Deletion／Protected Scope。**

**13\. Metadata Readback：確認 Document ID、Title、Parent、URL、MIME 仍符合原文件身分，Revision／modifiedTime 依實際修改更新，且沒有建立未授權的新 Drive 文件。**

**14\. Online Key Readback：至少回讀修改區前段、中段、後段或 Evidence／Navigation 區的代表性關鍵文字，證明正式雲端內容與 Candidate intent 一致。**

**15\. Backup Finalization：任務結束前確認最終保留的 Backup Copy 已位於 使用者指定且已驗證的 Google Drive 備份資料夾；工作區或其他本機備份只可作暫存，不得作唯一最終備份。**

**16\. Evidence：保存 Source／Backup／Candidate 識別、Hash（如適用）、Render QA、Structured Diff、Write／Readback、Before／After Revision、Unexpected Changes 與 Final Result。**

**Mode C Stop Rule：任何工具能力、file\_uri 契約、Revision、Boundary、Candidate 來源或原生文件身分無法確認時，停止並回報。除非使用者另行授權，不得因某個寫入策略失敗就自行切換成 update\_file raw-byte replacement、建立新 Google Docs、刪除原文件、改 Parent、改分享權限或其他替代交付策略。**

**Mode C Success Criteria：不是「Candidate 做完」也不是「Connector success」。只有原 Document ID 的線上內容完成 Readback／Verification／Integrity，且身分與 Protected Scope 正常，才可標記 VERIFIED\_COMPLETE。**

## 13｜Known Failure Modes 與 Anti-patterns

| Failure Mode | 風險 | 對應 Rule |
| :---- | :---- | :---- |
| Request Count Bias | 把一個 request 當成一個安全修改。 | ED-RISK-01／ED-UNIT-01 |
| Shallow Readback | 只確認新增文字存在，不確認下一章與完整 Sequence。 | ED-VERIFY-01／ED-READBACK-01 |
| Style-first Repair | 看到樣式異常就先修 Style，忽略可能的 Structure Corruption。 | ED-INTEGRITY-01／ED-STOP-01 |
| Repair Before Stop | 重大異常後先試修，導致 Revision 與受損狀態更複雜。 | ED-STOP-01／ED-ESCALATE-01 |
| Connector Success Bias | API 成功即宣告完成。 | GD-01 |
| First Read Bias | 第一次閱讀即下結論。 | Don’t Trust First Read |
| Memory Bias | 依記憶或摘要補寫遺失內容。 | ED-EVIDENCE-01 |
| Scope Expansion | Read-only 或小修任務順手改其他問題。 | Execution Boundary |
| Evidence Loss | 未保存 request、Boundary、Revision 與 Readback。 | ED-EVIDENCE-01 |

 

## 14｜每個 Write Task 的強制 Checklist  
□ 已完成 CSV。

□ 已依 Risk Level 完成 Backup Gate；L4／L5／Recovery Write 強制 BACKUP\_VERIFIED。

□ 已判定 Write Risk Level。

□ 已指定最低 Verification Level。

□ 已拆分 Structural Units。

□ 已指定 Target Boundary 與 Protected Scope。

□ L4／L5 已完成 Boundary Checklist。

□ 已指定 Readback Scope。

□ 同一環境可完成 Write → Immediate Readback → Verification；Minimal Repair 與 Localized Post-Write Correction 均只能在 07.3 對應 Eligibility 全部成立時使用。  
□ 若使用 Localized Post-Write Correction，只執行一次 bounded correction，且 correction 後已完成 Immediate Readback 與 Style／Paragraph／Neighbor／Sequence Verification。

□ 每個 Unit 後已立即回讀。  
□ 已完成文字、Style、Paragraph、Neighbor、Sequence／Integrity 驗證（依 Level）。  
□ 已保存必要 Evidence。

□ 沒有觸發 Verification Stop Rule。

□ 若觸發 Stop Rule，已停止並轉 Escalation／Recovery，而非先修看看。

□ 只有全部通過後才標記 VERIFIED\_COMPLETE。
