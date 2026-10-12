# 退回紙條 · BMI 計算機驗收結果 / 2026-10-12

給：隊員・太魯閣　　來自：領隊・洄瀾　　對象檔案：`workspace/outbox/20261012-bmi-calculator.html`

## 驗收怎麼做的 / How I checked

逐段對過程式邏輯與規格，並心算核對數值。**有一個擋下來的功能性 bug，請修好再交。**

## 通過的部分（不要動）/ Verified

- 公式與取值：BMI＝kg÷m²、四捨五入到小數一位 ✓；健康體重範圍＝18.5～24×m²（170 cm → 53.5～69.4 kg 核對無誤）✓
- 六級分界與邊界歸屬：24.0→過重、27.0→輕度肥胖、30.0→中度肥胖、35.0→重度肥胖 ✓
- 輸入防呆：空白、範圍外（50–250／10–300）、非數值都擋，不會出現 NaN／Infinity ✓
- 雙語：預設 `zh-Hant-TW`、切換鈕與整頁文字（含表格、免責、錯誤訊息）都有中英 ✓
- 隱私：無 localStorage、無任何網路請求 ✓；免責兩句齊全 ✓
- 單一 HTML、無外部資源、交接註解在 `</body>` 前 ✓；shared 與 picker v1～v4 原封未動 ✓

## 要改的（擋下來的 bug）/ Must fix

**體位分類徽章顯示 `undefined`。**

- 位置：`renderResult` 裡（約第 385 行）動態組 key：`"badge" + 駝峰(category)`，例如 `badgeUnderweight`、`badgeNormal`、`badgeMildObesity`。
- 但 I18N（zh、en 兩組）裡的實際 key 是縮寫版：`badgeUnder`、`badgeNorm`、`badgeOver`、`badgeMild`、`badgeMod`、`badgeSev`。
- 六個全部對不上 → `t[badgeKey]` 是 `undefined` → 徽章文字永遠變成字串「undefined」。這是必現 bug，每一種分類都會中。
- 修法任選一種，自己決定：
  1. 建一張對照表（category → I18N key）明確映射；或
  2. 把 zh／en 的 key 改成動態組法能對上的全名（`badgeUnderweight` 等六個，兩組都要改）。
- 注意：切換語言時 `applyLanguage` 會用 `lastResult` 重畫結果，徽章也要跟著換成新語言的文字。

## 怎樣算修好 / Fixed looks like

- 另存新檔：`workspace/outbox/20261012-bmi-calculator-v2.html`（**不要動 v1**，留歷史版本）。
- 用身高 170 cm 實測六個分類，徽章都顯示正確中文（切到 English 後顯示英文）：
  - 50 kg → 過輕（BMI 17.3）
  - 65 kg → 正常（22.5）
  - 70 kg → 過重（24.2）
  - 80 kg → 輕度肥胖（27.7）
  - 90 kg → 中度肥胖（31.1）
  - 102 kg → 重度肥胖（35.3）
- 其餘段落照抄 v1，不要順手改壞已通過的部分。
- `</body>` 前保留一行交接句（做了什麼、哪裡要注意、能不能直接用）。

## 做完之後 / After

放在 outbox 就**停**，回報「BMI v2 完成，請小隊長請領隊複驗」。不要自己回頭找領隊。
