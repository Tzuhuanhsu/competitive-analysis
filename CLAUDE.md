# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 這是什麼

這不是程式碼專案，而是一個**競品分析（competitive analysis）文件庫**，用於拆解他廠 SLOT（老虎機）遊戲的玩法機制與玩家體感設計。沒有 build / test / lint 流程；工作內容是閱讀、撰寫與整理分析文件與截圖素材。正式報告以各競品資料夾內的 PDF 為主，repo 內的 Markdown 是與 Claude 溝通用的初版草稿。

## 目錄慣例

每個競品各佔一個頂層資料夾，以遊戲名稱命名（例：`SugarTeddy/`），內部結構：

```
<遊戲名>/
  <遊戲名>.pdf   正式分析報告（最終產出，以此為準）
  Design.md      初版草稿，用於與 Claude 溝通分析方向
  素材/          截圖，檔名以「所描述的體感」命名（中文）
```

**PDF 才是正式的分析報告**；`Design.md` 只是與 Claude 溝通用的初版文件。因此：

- 討論「這份分析怎麼寫的 / 結論是什麼」時，以 PDF 為準；`Design.md` 可能較舊或較粗略。
- 修改 `Design.md` 不等於更新報告——正式內容的修訂發生在 PDF，不在 repo 內由 Claude 直接編輯。
- 若 `Design.md` 與 PDF 有出入，不要逕自「修正」`Design.md`，先向使用者確認哪邊才是現況。

## 正式報告的內容架構

`SugarTeddy/SugarTeddy.pdf`（8 頁，A4 橫向，深色簡報版式，由網頁列印產生）是目前唯一的正式報告，章節編號即為分析框架，新競品比照：

| 章節 | 內容 |
| --- | --- |
| 封面 | 遊戲名、廠商、Release、資料來源（實機試玩截圖） |
| `01 / SPEC` | 規格表：輪盤、得獎方式、落消、乘倍、Free Game、Extra Bet |
| `02 / STRUCTURE` | 核心體驗＝可疊加的期待感層（倍數符號 / 連續消除 / 小熊收集），強調 A+B+C 各自獨立觸發、同時出現時相疊 |
| `03 / RHYTHM` | 單次 Spin 的時間軸（T1 盤面落下 → T2 首次消除 → T3 補落與 Combo → T4 倍數累加 → T5 進度回饋） |
| `04 / MULTIPLIER` | 倍數機制拆解：累積而非單次結算 |
| `05 / COLLECTION` | 收集系統的狀態演進（STATE 1 進度可視化 → STATE 2 機率預告 → STATE 3 隨機獎勵） |
| `06 / RETENTION` | 收集軌承擔的留存作用：安撫、認可、續玩動機、期待回饋 |
| `07 / TAKEAWAYS` | 可借鏡設計，卡片式條列 |

比 `Design.md` 多出來的關鍵資訊（以 PDF 為準）：得獎方式為 8 個以上相同符號消除、Free Game 期間**倍數累積不歸零**、Free Game 期間收集軌仍持續累積。

`Design.md` 對應的是 PDF 的 `01`／`02`；`03`–`07` 只存在於 PDF。

## 讀取 PDF

`Read` 工具需要 poppler 的 `pdftoppm`。本機已用 winget 安裝 `oschwartz10612.Poppler`，執行檔在：

```
%LOCALAPPDATA%\Microsoft\WinGet\Packages\oschwartz10612.Poppler_*\poppler-*\Library\bin
```

該路徑已加入使用者 PATH。若 `Read` 仍回報 `pdftoppm is not installed`，表示 Claude Code 行程的 PATH 是安裝前的舊值——重啟 Claude Code 即可，或改用手動轉圖再讀：

```powershell
$env:PATH = "$env:LOCALAPPDATA\Microsoft\WinGet\Packages\oschwartz10612.Poppler_Microsoft.Winget.Source_8wekyb3d8bbwe\poppler-25.07.0\Library\bin;$env:PATH"
pdftoppm -r 110 -png <in.pdf> <輸出前綴>   # 再用 Read 讀產生的 PNG
```

素材檔名本身就是分析的一部分——例如 `消除連續感1.png`、`倍數符號期待2.png`、`小熊收集3.png`。命名是「機制 + 玩家感受 + 序號」，同一組體感用同名編號成序列以呈現演繹過程。新增截圖請延續此命名法，不要改成英文或流水號。

## 初版草稿（Design.md）寫法

`Design.md` 的作用是把觀察快速記下、與 Claude 對焦分析方向，之後才整理進 PDF。`SugarTeddy/Design.md` 是格式範本，新增競品時比照：

1. `# SLOT 分析` → `## 遊戲:<廠商> <遊戲名>`
2. `### 1. 遊戲介紹` — 條列式規格：輪盤尺寸、落消 / 連線機制、倍數區間、Free Game 型態、Extra Bet 等付費選項。
3. `### 2. 遊戲特色` — 先條列「期待感」來源，再用散文段落說明**節奏**與**心理設計**：期待感如何堆疊、等待感如何被壓縮、未中獎時如何安撫玩家。

分析的核心視角是**玩家情緒曲線**而非數學模型：關注多重期待感的疊加（符號繼續消除 × 倍數球落下 × 高倍數）、收集感、驚喜感、以及演繹節奏對等待感的影響。撰寫時保持繁體中文，沿用既有詞彙（落消、期待感、體感、演繹、收集感）。

## 語言

文件與檔名一律使用繁體中文；回覆使用者亦以繁體中文為主。
