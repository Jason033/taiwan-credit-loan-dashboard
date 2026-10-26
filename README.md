# 台灣個人信貸利率觀察

[開啟互動網站](https://taiwan-credit-rate-explorer.hazy-skunk-5453.chatgpt.site)（沿用目前的私有存取權限）。

資料快照：2026-10-26；1,834 筆案例，其中 1,265 筆有可辨識利率、1,208 筆可計算扣 I 利差。

## 專案內容

- `index.html`：免建置的單頁網站，包含銀行利率分布、職業利率分布、整體利率區間與初始／最終利率比較。
- `data.json`：網站使用的匿名化案例分析資料及統計口徑。
- 銀行圖與職業圖分開篩選，各自使用欄位可用的案例；利率可切換絕對年利率與扣 I 利差。

## 本機開啟

因瀏覽器會限制直接讀取本機 JSON，請在專案根目錄啟動靜態伺服器：

```bash
python -m http.server 8000
```

再開啟 <http://localhost:8000>。網站沒有後端或安裝步驟。

## 資料欄位

利率以百分比數值儲存，例如 `3.25` 代表年利率 3.25%。缺值為 `null`。

| 欄位 | 說明 |
| --- | --- |
| `bank` | 銀行 |
| `nominalRate` | 可辨識的絕對年利率 |
| `initialRate` / `finalRate` | 初始／最終利率 |
| `stage` | 個人估算、核准／承作或其他狀態 |
| `occupation` | 寬鬆歸類的職業類別 |
| `grade` | 案例資料等級 A／B／C |
| `comparisonYear` | 扣 I 計算採用的比較年份 |
| `annualI` | 該年份的共同參考 I 值 |
| `spreadRate` | 扣 I 後利差；通常為 `nominalRate - annualI` |
| `initialSpreadRate` / `finalSpreadRate` | 初始／最終利率扣 I 後的利差 |
| `iValueBasis` | I 值來源方式：貸款年、發文年、原文加碼或無可用值 |
| `sourcePostYear` | 原文發文年份；部分 Dcard 年份依貼文編號估算 |
| `explicitLoanYear` / `explicitLoanMonth` | 原文有明示時記錄的貸款年月 |
| `comparisonYearBasis` | 比較年份採用原文貸款年、發文年估值或無可用年份 |
| `rateExtractionBasis` | 利率採原文可辨識值或區間中點 |
| `sourcePostYearBasis` | 發文年份取自索引／來源日期或貼文編號估年 |
| `occupationBasis` | 職業分類依原文欄位或工作背景線索 |

完整計算規則保存在 `meta`：來源年份優先用於跨年比較；貸款年與發文年相差不超過 2 年時採發文年，差距較大則保留原文貸款年。I 值使用郵政二年期定儲機動利率作共同參考，按適用日期加權；不同銀行合約可能採用不同指標。

## 資料範圍

此資料檔供網站統計使用，不含原文全文、貼文連結、姓名或帳戶識別資訊。完整銀行分類案例與原文連結仍保存在 [Google Drive 資料夾](https://drive.google.com/drive/folders/1JAbEvcazEYJEGqDL1y083rND_VCnS88g)。網站與資料儲存庫維持私有。
