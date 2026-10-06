# 社團檔案整理報告 (Club Files Organization Report)

## 一、 整理成果摘要
- **原始檔案路徑：** `practice/01-club-files/input`
- **整理輸出路徑：** `practice/01-club-files/output`
- **處理檔案總數：** 12 份輸入檔案，全部保留副本複製至分類目錄，**原始檔案未做任何修改或刪除**。
- **產出清單：** `manifest.json`（12 筆對照記錄）、`report.md`（本報告）。

---

## 二、 分類架構與檔案清單

| 分類資料夾 | 檔案名稱 | 說明 |
|---|---|---|
| **`proposals/`**（企畫與方案） | `proposal_final.txt`<br>`proposal_final2.txt`<br>`rain_plan.txt` | 企畫第一版草案、企畫第二版草案、雨天應變備案 |
| **`meetings/`**（會議與待辦） | `meeting_notes.txt`<br>`next_steps.txt` | 籌備會議討論筆記、後續方案比較與行動項目 |
| **`logistics/`**（物資與預算） | `budget_draft.txt`<br>`equipment_list.txt`<br>`equipment_backup.txt` | 活動紙張預算草案、器材需求清單、器材備份清單 |
| **`promotion/`**（文宣推廣） | `announcement.txt`<br>`announcement_copy.txt`<br>`poster_text.txt`<br>`feedback_questions.txt` | 活動公告通知、公告副本、宣傳海報文案、回饋問卷題 |

---

## 三、 疑似重複檔案分析

透過內容雜湊比對（MD5），確認以下兩組檔案內容完全相同：
1. **活動公告：**
   - `announcement.txt` 與 `announcement_copy.txt`
   - 雜湊值：`8A382293D766BE1CCC1408F510A2118C`
   - 處理方式：依規範均保留副本並歸類於 `promotion/`，建議後續確認是否只需保留一份。
2. **器材清單：**
   - `equipment_list.txt` 與 `equipment_backup.txt`
   - 雜湊值：`51C6AE39FA9250CD545E74224041F6F5`
   - 處理方式：依規範均保留副本並歸類於 `logistics/`，已註明為備份關係。

---

## 四、 名稱相近但內容不同版本

- **檔案對比：**
  - `proposal_final.txt`（企畫第一版）：規劃「戶外活動，30分鐘」，註記「尚未定案」。
  - `proposal_final2.txt`（企畫第二版）：規劃「室內活動，20分鐘」，註記「仍待討論」。
- **判斷原則：**
  - **切勿**單純依據檔名含有 `final`、`final2` 或作業系統修改時間判定誰是最終版。
  - 兩份企畫之活動型態（室內 vs 室外）、活動時間長度（20分鐘 vs 30分鐘）完全不同，且文件內容皆明確記載「尚未定案 / 待討論」。
  - 處理方式：兩版本皆完整保留於 `proposals/` 目錄，交由幹部會議決策。

---

## 五、 待確認問題（待幹部決策）

1. **活動企畫案最終決策：** 需於下次會議比對第一版（戶外 30 分鐘）與第二版（室內 20 分鐘）之可行性並正式定案。
2. **預算審核：** `budget_draft.txt` 提及「紙張預算模擬100，尚未核定」，需確認正式經費是否通過。
3. **時間與地點資訊：** `announcement.txt` 提及「時間地點尚未決定」，待企畫拍板後需補齊並發布。

---

## 六、 檢查紀錄

### 實際做過的檢查
- [x] 檔案總數驗證：輸入 12 個檔案，輸出分類目錄完整複製 12 個檔案。
- [x] 原始檔案保護：`input/` 目錄內 12 個檔案與時間戳記完全未受影響。
- [x] 檔案內容完整性：透過 SHA-256 / MD5 比對每一份複製後檔案與原始檔案內容，雜湊值 100% 吻合無損毀。
- [x] 格式規範檢驗：`manifest.json` 符合最外層 12 筆物件陣列格式，各欄位（`source`, `destination`, `reason`）齊全；`report.md` 包含分類、重複及待確認問題。

### 尚未確認（需人工判斷）的部分
- [ ] 幹部尚未開會決定究竟採用第 1 版還是第 2 版企畫。
- [ ] 是否刪除完全重複的 `announcement_copy.txt` 與 `equipment_backup.txt`（目前依指示安全保留）。
