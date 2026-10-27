# 台灣個人信貸利率觀察

**GitHub Pages 網址（啟用後）：** `https://jason033.github.io/taiwan-credit-loan-dashboard/`  
**舊站（ChatGPT Sites）：** <https://taiwan-credit-rate-explorer.hazy-skunk-5453.chatgpt.site>（不會隨 GitHub 提交自動更新）  
**資料快照：** 2026-10-26 · **完整案例：** 1,834 筆  
**Excel：** [下載完整案例與摘要工作表](data.xlsx)

本專案整理網路上的個人信貸分享，讓使用者查看利率落點、各銀行分布、職業分布，以及案例中較早與後來提到的利率變化。資料是個人經驗分享，不是銀行官方核貸資料，也不能預測個人可取得的利率。

## 網站怎麼看

- **利率落點：** 看所有可用案例落在哪些利率區間。
- **各銀行利率分布：** 每家銀行獨立整理，只需要案例有銀行和利率，不要求職業資料完整。
- **職業利率分布：** 每種職業獨立整理，不要求銀行資料完整；不清楚的職業另列。
- **送審與議價前後的利率變化：** 比較案例較早記載的利率與後續利率中位數。每篇案例的實際階段可能不同，請以原文描述為準。
- **扣 I 開關：** 以案例適用年份的郵政二年期定儲機動利率作共同參考，換算利差，方便比較不同年份的案例。網站會標出目前 I 值；歷史案例仍使用各自年份的 I 值。
- **下載 Excel：** 網站頁尾可下載同一份多工作表活頁簿。網址也會列在每筆案例的原文網址欄，若網址失效可複製到瀏覽器。

## Excel 工作表

`data.xlsx` 包含六張工作表：

| 工作表 | 內容 |
| --- | --- |
| 閱讀指南 | 資料筆數、網站、索引與 I 值來源 |
| 案例資料 | 1,834 筆案例、發文年月、利率、分類與原文網址 |
| 銀行摘要 | 各銀行案例量與利率中位數 |
| 職業摘要 | 各職業案例量與利率中位數 |
| I值參考 | 案例比較年份、採用的 I 值與目前參考 I 值 |
| 欄位說明 | 欄位名稱、單位與整理方式 |

利率欄以百分比格式顯示；發文年月無法辨識時寫「沒有」。原文網址完整保留在單一儲存格，不以換行或截斷符號代替。

## 資料與計算

- 目前快照有 1,834 筆案例，其中 1,265 筆有可辨識利率，1,208 筆可計算扣 I 利差。
- 利率以原文的名目年利率為準；約數照錄，只有區間時取中點，明確的後續核准數字優先。APR 不代替名目利率。
- 年份不明時，扣 I 比較使用貼文年份；原文貸款年與貼文年相差不超過兩年時使用貼文年，差距更大時保留原文貸款年。部分 Dcard 年份依貼文編號估算，重點是保留可用案例。
- 目前共同參考 I 值為 1.720%（資料快照截至 2026-10-26）。跨年比較時，每筆案例扣除其適用年份或月份的 I 值；目前 I 不會套用到所有歷史案例。
- 銀行與職業圖各自使用可用資料，不只取兩種欄位都有的交集。職業可依原文與工作背景線索寬鬆歸類。
- 部分案例可能沒有可辨識利率、年份、職業或貼文月份；缺少時不虛構精確值。Excel 原文網址可回看個別分享。

目前 I 值來源：[台新銀行利率頁面](https://www.taishinbank.com.tw/TSB/personal/loan/ntd-loan-rate/detail/)；歷史參考：[郵政二年期定儲機動利率歷史表](https://web.taishinbank.com.tw/TSB/export/sites/TSB/files/loan/_20260921Adjustable-Rates-for-Consumer-Loans.pdf)。完整分類文件與來源連結保存在 [Google Drive 資料夾](https://drive.google.com/drive/folders/1JAbEvcazEYJEGqDL1y083rND_VCnS88g)，總索引在[這裡](https://docs.google.com/document/d/1PXqz49k8Z9wfauG0LLJFny2BAQjyn_zhsXLXKFDFqGM/edit)。

## 專案檔案

- `index.html`：互動圖表與操作介面。
- `data.json`：網站使用的匿名化分析資料。
- `data.xlsx`：供閱讀與篩選的多工作表資料活頁簿。

GitHub 儲存庫維持私有；互動網站可由任何取得網址的人開啟。

## 網站訪客計數

- 頁尾顯示小型「訪客 X 人」，統計全站累計獨立訪客（UV），不以每次重新整理作為一次訪問。
- 使用外部 [Busuanzi 計數 API](https://bsz.saop.cc/en) 保存全站統計。第一次開啟呼叫 `POST /api`；同一瀏覽器記住已計數狀態，之後只用 `GET /api` 讀取最新累計值。
- API 也會做伺服器端訪客去重；同一人換瀏覽器、裝置、網路或清除識別資料時，仍可能被視為不同訪客。因此數字是估計值，無法保證每個自然人終身只算一次。
- 外部服務為辨識訪客會收到必要的連線資訊（例如 IP 位址與瀏覽器資訊），本站不自行儲存個人身分資料。服務無法連線時顯示「—」，不會捏造數字。

## GitHub Pages 發布

此專案已設定 GitHub Actions 自動部署工作流程：[`deploy-pages.yml`](.github/workflows/deploy-pages.yml)。只有 `index.html`、`data.json`、`data.xlsx` 會打包成公開網站，更新 `main` 便自動重新部署。

**首次啟用設定（由儲存庫管理者執行一次）：**

1. 前往 **Settings → General → Danger Zone → Change repository visibility**。若帳號為 GitHub Free，選 **Public**（公開整個原始碼與資料檔）；若帳號支援私有儲存庫 Pages，則可保留 Private。
2. 前往 **Settings → Pages → Build and deployment → Source**，選 **GitHub Actions**。
3. 如自動部署工作流程先前因 Pages 未啟用而失敗，前往 **Actions → Deploy credit loan dashboard to GitHub Pages → Run workflow** 重新執行。
4. 發布成功後，網址為 <https://jason033.github.io/taiwan-credit-loan-dashboard/>。

**狀態：** 工作流程已提交，但尚未確認網站已啟用及部署完成。GitHub Pages 網站即使使用私人儲存庫，也可能對外公開。

**訪客計數：** 網站頁尾顯示累計 UV 估計值，使用外部計數 API，並以瀏覽器儲存狀態避免一般重新整理重複送出計數。

## 本機開啟

在專案根目錄啟動靜態伺服器：

```bash
python -m http.server 8000
```

再開啟 <http://localhost:8000>。網站沒有後端或安裝步驟。
