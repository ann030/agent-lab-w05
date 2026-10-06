# My lab evidence / 我的實作紀錄

Use a group code, not real names or student IDs in shared files. / 共用檔只寫組別代碼，不寫姓名或學號。

- Group code / 組別：W05-01
- Tool / 工具：Antigravity
- Route / 路線：individual 個人
- Tasks completed / 完成題目：A, B, C, D
- Material / 素材：NDHU classroom tasks 東華課堂版
- For original-pack work: task number, author/source link and version / 原版實作：無（使用東華課堂版）
- My role and what I checked / 我的角色與實際檢查：操作與驗收；檢查輸入與輸出目錄、原檔完整性、雙向雜湊比對、活動挑選器各項條件邏輯、器材記錄清洗結果與退回計畫理由。

## Scope and plan / 範圍與計畫

Allowed input and output folders / 可讀取與輸出的資料夾：
- Task A: `practice/01-club-files/input` -> `practice/01-club-files/output`
- Task B: `practice/02-campus-picker/activities.json` -> `practice/02-campus-picker/output/index.html`
- Task C: `practice/03-equipment/equipment.json` -> `practice/03-equipment/output/`
- Task D: `practice/04-review/bad-plan.txt` -> `practice/04-review/my-rejection.md`

What I asked for / 原始需求：
- A: 盤點 12 個文字檔，不以 final 判定定稿，原檔不動，產出分類副本、manifest.json 與 report.md。
- B: 製作單頁離線活動挑選器，符合三項條件隨機挑選、保留最近 5 筆紀錄、重設篩選與雙語切換。
- C: 清理器材記錄，統一狀態、去除前後空白、保留原來源列號與異常數值，回報問題。
- D: 審查模擬計畫並寫出退回原因與替代做法。

What I checked before execution / 動手前我檢查了什麼：
- 確認工作目錄與權限，不碰 Downloads 或專案外的資料夾。
- 確認原始輸入檔案為唯讀，不執行任何破壞性刪除。
- 檢視 AI 提出的白話計畫，確認未擅自擴大範圍或修改原檔後才允許執行。

## Tests actually performed / 我真的做過的測試

| Test / 測試 | Expected / 預期 | Observed / 實際 | Evidence / 證據 |
|---|---|---|---|
| 1. Task A 雜湊與原檔檢查 | 12 個原檔皆保留且內容不變，output 12 份副本雜湊 100% 一致 | 原檔完全未動，副本 SHA-256 與原檔完全吻合 | 經腳本比對 12 筆 MD5/SHA256 均一致，產出 manifest.json 與 report.md |
| 2. Task B 條件篩選（室內/15分/低） | 僅可能選到 A01, A02, A03, A04 | 隨機挑選結果皆在 A01~A04 範圍內，無越界 | 瀏覽器實測與 Node.js 篩選函數驗證通過 |
| 3. Task B 嚴格比對無符合（室外/15分/中） | 顯示「沒有符合條件的活動」，不放寬條件 | 頁面清楚呈現紅色「沒有符合條件的活動」，不擅自偷改條件 | 瀏覽器實測與邏輯測試通過 |
| 4. Task B 唯一符合（室外/30分/中） | 每次挑選均只能是 A09 | 每次點擊皆固定抽出 A09 | 瀏覽器實測與邏輯測試通過 |
| 5. Task B 歷史紀錄與重設 | 抽 6 次只留最近 5 次；重設篩選時歷史仍在 | 成功抽滿 6 次後，畫面只保留最新 5 筆；點擊重設篩選後條件恢復預設，歷史清單未被清除 | 瀏覽器介面實測確認 |
| 6. Task C 資料清理有效筆數 | 10 列原始資料去除 1 列全空後為 9 列有效 | 輸出 9 筆，source_row: 6 移除，異常值均保留 | normalized.json 與 issues.md 驗收完成 |

## One revision / 一次修改

Before / 原來的情況：
Task B 第一版（v1）僅能透過滑鼠點擊「幫我選」按鈕進行隨機挑選，連續測試或手持鍵盤操作時較不便利。

Request / 我提出的修改：
新增鍵盤快捷鍵支援，按下鍵盤 Space（空白鍵）或 Enter 鍵即可快速觸發隨機挑選，並在介面提供快捷鍵提示與按鈕點擊微縮動態回饋，切換英文時提示同步切換。

After and retest / 修改後與重測結果：
在 `output/index.html` 成功加入鍵盤監聽事件與 i18n 提示。打開網頁後直接按空白鍵或 Enter 鍵即可順利抽卡，且在下拉選單展開時不誤觸，切換英文時顯示 `⌨️ Shortcut: Press Space or Enter to pick an activity`。

New requirement or defect? / 新需求還是原規格未做到？
屬於「新需求」（原規格已有完整的滑鼠按鈕挑選功能，快捷鍵為提升操作體驗與無障礙操作之新增功能）。

## One rejection / 一次退回

Which action I reject and why / 退回哪個動作、為什麼：
退回 `bad-plan.txt` 中的「整理整個 Downloads 資料夾」、「擅自刪除重複檔」、「把 final2 當最新版」、「找不到資料補合理值」以及「自動公開成果」。因為這些動作擅自擴大操作範圍至個人隱私目錄、破壞原始資料、主觀臆測資料真實性，且未經授權公開發布，違反最小權限與安全原則。

An acceptable alternative / 可以怎麼改：
嚴格限定只讀取與操作指定題目目錄；原檔保持唯讀且完全保留副本；依內容比對差異而非憑檔名猜測定稿；缺漏異常值原樣保留並以報告回報；成果僅存放本地 output 目錄，絕不自動連網公開。

## Still unverified / 還沒驗證

What I cannot claim is complete / 哪些事不能說已完成：
1. Task A 的兩版企畫（室外 30 分鐘 vs 室內 20 分鐘）與預算（100 單位）尚未經社團幹部正式開會定案。
2. Task B 的隨機挑選在有限測試次數下不能證明統計學上的機率絕對公平，僅驗證了條件篩選與抽中邏輯符合規格。
3. Task C 中重複的 EQ01 筆數與衝突的 EQ02 數量（2 支 vs 3 支）尚未經實體庫存盤點查核。
