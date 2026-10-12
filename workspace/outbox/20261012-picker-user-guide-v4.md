# 「課間我想做什麼？」挑選器使用說明

## 這是什麼

一個在課間空檔挑選合適活動的網頁工具，雙擊 `campus-picker.html` 即可開啟（README：Double-click it to play）。

> 提醒：頁面活動為「虛構教學活動，不是學校正式公告」（Fictional teaching activities; not an official university announcement.）。

## 怎麼用

1. **挑選三個條件**（各為單選）：
   - **Location／地點**：All／全部（預設）、Indoor／室內、Outdoor／室外
   - **Available time／可用時間**：15／30（預設）／60 分鐘
     - 規則：只會從「活動所需時間 ≤ 你選的時間」的活動裡挑。
   - **Energy／體力**：All／全部（預設）、Low／低、Medium／中

2. **按「Pick for me／幫我選」**：系統從符合條件的活動中隨機抽一個。

3. **看結果框**：
   - 一開始顯示：「選好條件，再按『幫我選』。」
   - 抽中時顯示：編號 · 名稱 · 所需分鐘 · 地點 · 體力。
   - 沒有符合時顯示：「沒有符合條件的活動。」——這時條件保持不變，歷史也不動。例如選「室外＋15 分鐘＋中體力」就沒有符合（室外＋中體力只有「在合適位置快走」，需 30 分鐘）。

4. **看紀錄**：「最近 5 次（最新在上）」只記成功抽中的，最新排最上面；還沒有紀錄時顯示「還沒有紀錄。」。

5. **三個輔助按鈕**：
   - **切換語言**（英文介面顯示「中文」，中文介面顯示「English」）：即時切換整頁介面。
   - **Reset filters／重設條件**：條件回預設（All／30／All），結果框回提示句，歷史保留。
   - **Clear history／清除紀錄**：清空歷史清單。

## 12 個活動一覽

| 編號 | 活動 | 所需時間 | 地點 | 體力 |
| :--- | :--- | :--- | :--- | :--- |
| A01 | 整理書包／Organize your bag | 10 分鐘 | Indoor／室內 | Low／低 |
| A02 | 畫一張小卡／Draw a small card | 15 分鐘 | Indoor／室內 | Low／低 |
| A03 | 寫三句讀書筆記／Write three study notes | 10 分鐘 | Indoor／室內 | Low／低 |
| A04 | 安靜讀兩頁書／Read two pages quietly | 15 分鐘 | Indoor／室內 | Low／低 |
| A05 | 排好明日待辦／Plan tomorrow’s tasks | 20 分鐘 | Indoor／室內 | Low／低 |
| A06 | 整理本機練習檔／Organize practice files | 30 分鐘 | Indoor／室內 | Medium／中 |
| A07 | 在合適位置慢走／Take a gentle walk in a suitable area | 15 分鐘 | Outdoor／室外 | Low／低 |
| A08 | 觀察天空並畫草圖／Observe the sky and sketch | 20 分鐘 | Outdoor／室外 | Low／低 |
| A09 | 在合適位置快走／Take a brisk walk in a suitable area | 30 分鐘 | Outdoor／室外 | Medium／中 |
| A10 | 規劃小組練習／Plan a group exercise | 45 分鐘 | Indoor／室內 | Medium／中 |
| A11 | 記錄自然色彩／Record colors in nature | 45 分鐘 | Outdoor／室外 | Low／低 |
| A12 | 構思下一次社團活動／Brainstorm a future club activity | 60 分鐘 | Indoor／室內 | Medium／中 |

以上 12 個活動寫死在挑選器裡；幫我選只會從符合你條件的活動中隨機抽一個。

## 三件做不到的事

1. **記不住你的紀錄**——歷史只存在記憶體裡（程式註解：not saved after reload），重新整理或關掉網頁就沒了。
2. **不能加、改、刪活動**——12 個活動寫死在頁面裡（與 `activities.json` 完全相同），沒有任何編輯功能。
3. **不會推薦時間不夠的活動**——篩選條件是「所需時間 ≤ 你選的時間」，不夠就是顯示「沒有符合條件的活動。」，不會硬塞。

---

以上全部對回 `campus-picker.html`、`activities.json`、`README.md` 驗證過；這是虛構教學用的活動資料。

> **交接**：已在 v3 基礎上於「怎麼用」之後插入「12 個活動一覽」表格（12 列完整對照 activities.json 順序與內容），其餘段落一字未動，v1～v3 均完整保留，可直接使用。
