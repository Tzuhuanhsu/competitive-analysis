# competitive-analysis

SLOT（老虎機）遊戲競品分析文件庫。拆解他廠遊戲的玩法機制與玩家體感設計，重點放在**玩家情緒曲線**——期待感如何堆疊、演繹節奏如何壓縮等待感、未中獎時如何安撫玩家——而非數學模型。

## 分析報告

**正式的分析報告以 PDF 為主**；同目錄的 `Design.md` 只是用來與 Claude 溝通的初版草稿，不是最終產出。

| 遊戲 | 廠商 | 分析報告（正式） | 初版草稿 | 素材 |
| --- | --- | --- | --- | --- |
| 糖果泰迪熊 x1000（Sugar Teddy） | BNG | [SugarTeddy.pdf](SugarTeddy/SugarTeddy.pdf) | [Design.md](SugarTeddy/Design.md) | [截圖](SugarTeddy/素材) |

報告章節即分析框架：`01 SPEC` 規格總覽 → `02 STRUCTURE` 三層可疊加的期待感 → `03 RHYTHM` 單次 Spin 的期待感節奏 → `04 MULTIPLIER` 倍數累積機制 → `05 COLLECTION` 收集系統的三種演繹 → `06 RETENTION` 收集軌承擔的四件事 → `07 TAKEAWAYS` 可借鏡設計。

## 目錄慣例

每個競品各佔一個頂層資料夾，以遊戲名稱命名：

```
<遊戲名>/
  <遊戲名>.pdf   正式分析報告（最終產出，以此為準）
  Design.md      初版草稿，用於與 Claude 溝通分析方向
  素材/          截圖，檔名以「所描述的體感」命名
```

素材檔名本身就是分析的一部分，採「機制 + 玩家感受 + 序號」命名（例：`消除連續感1.png`、`倍數符號期待2.png`），同一組體感以同名編號成序列，用來呈現演繹過程。

## 初版草稿格式

`Design.md` 用來把觀察快速記下、與 Claude 對焦分析方向，內容之後整理進 PDF。以 [SugarTeddy/Design.md](SugarTeddy/Design.md) 為範本：

1. **遊戲介紹** — 條列式規格：輪盤尺寸、落消 / 連線機制、倍數區間、Free Game 型態、Extra Bet 等付費選項。
2. **遊戲特色** — 先條列期待感來源，再以段落說明節奏與心理設計。
