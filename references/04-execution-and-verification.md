> 定沄整合設計工作室｜SOP01 公開衍生稿 0.1.0。
> [Skill 入口](../SKILL.md) · [章節總覽](../README.md#chapters) · [任務契約](../templates/task-contract.md) · [授權](../LICENSE)

# Part D｜Execution & Verification
適用：逐 Unit Write、Readback、Integrity、Evidence 與完成判定。

## 08｜Execution、Readback、Integrity 與 Evidence

### 08.1｜Execution Workflow
1. 完成 CSV、Backup Gate、Risk Classification 與 Verification Plan。

2. 定位 Target Boundary，建立 Before Snapshot。

3. 依 Structural Unit 拆分 Write。

4. 一次執行一個 Write Unit。

5. 立即回讀該 Unit 與要求的 Readback Scope。

6. 完成對應 Verification Level。

7. 若通過，保存 Evidence 後再進下一 Unit。

8. 若不通過，先判斷 defect 是否完整符合 07.3 Localized Post-Write Correction Eligibility；符合者只允許一次 bounded correction → Immediate Readback → Verification，PASS 後才可繼續後續已授權 Unit。不符合 Eligibility，或一次 correction 後仍 FAIL，立即觸發 Stop Rule，不得先進下一 substantive Unit。

9. 所有 Units 完成後執行完整 Structure Integrity Check。

10. 全部驗證通過後才可標記 VERIFIED\_COMPLETE。

若已核准 Task Package 指定 Adaptive Chunked Execution，chunk 邊界、逐階段授權與停止條件必須由任務負責人提供；本 Skill 只負責每個 authorized Docs chunk 的實際 modification、Immediate Readback 與 verification mechanics，並持續遵守本文件的 Structural Unit／Risk／Integrity 規則。缺少必要 chunk 契約時先補齊，不由 AI 自行推定。

### 08.2｜Readback Scope Rule【ED-READBACK-01】

| Risk | 最低 Readback Scope |
| :---- | :---- |
| L1 | 目標文字＋前後一句 |
| L2 | 完整 Paragraph Unit＋相鄰 Unit |
| L3 | 全部修改 Units＋前後各一個 Boundary |
| L4 | 上一個 Heading → 修改區 → 下一個 Heading＋至少一個後續 Unit |
| L5 | 上一個安全 Anchor → 完整修改序列 → 下一章／Catalog＋至少兩個後續 Units |



### 08.3｜Structure Integrity Check【ED-INTEGRITY-01】
□ Heading

□ Paragraph

□ Sequence

□ Boundary

□ Duplicate

□ Missing

□ Merge

□ Unexpected Deletion

□ Protected Section／Scope

### 08.4｜Evidence Preservation【ED-EVIDENCE-01】

#### 08.4.1｜Evidence Lifecycle & Mapping
Evidence Lifecycle：Capture → Identify → Link → Verify → Publish → Reuse／Archive。證據若只存在聊天、沒有 Canonical Reference，視為 PARTIAL。

Evidence Mapping、Task Mapping、Rule Mapping 與 Cross-document Mapping 必須可相互追溯：Task → Write Unit → Evidence → Finding → Rule／Publication。

| Evidence 類型 | Canonical Reference | 對應關係 |
| :---- | :---- | :---- |
| Before／After Snapshot | Document ID＋Revision＋Target／Boundary＋時間 | Task ID／Write Unit／Boundary |
| Request Evidence | Request Type＋Target＋requiredRevisionId | Task ID／Authorization |
| Verification Evidence | Readback Scope／Sequence／Error Scan／Report | Acceptance／V-Level |
| Recovery Source | Source ID＋Role＋Status＋限制 | 待復原 Structural Unit |
| Publishing Evidence | Docs Revision／Publication Evidence | Formal Publication Status |
| Rule Evidence | Finding ID＋Postmortem＋Rule Reuse Result | Rule ID／Version |

L4／L5 強制保存；L1～L3 依 Task 需求保存。

- Request type／Action name。

- Target 與定位 Anchor／Boundary。

- Write Unit 清單。

- Before Snapshot。

- After Snapshot／Readback。

- Before／After Revision。

- Verification Level 與結果。

- Backup ID。

- 尚未驗證項目與 Stop Point。

***Decision Landmark｜任何 Verification／Integrity 失敗，立即進入 09；不得先修看看。***
