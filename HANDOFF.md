# 專案交接摘要 — 下一次對話從這裡開始

最後更新：2026-05-08

## 🌐 專案
- **GitHub repo：** https://github.com/bole0918/Virology-Lab
- **正式網站：** https://bole0918.github.io/Virology-Lab/
- **本地路徑：** `~/Documents/projects/Virology-Lab/`

## 📦 已完成的功能

### 主站
- ✅ 首頁 hero 升級（漂浮病毒粒子、漸層名字、stats 列、scroll 提示、動畫按鈕）
- ✅ PI 頭像放上實際照片（從 Google Sheets `members.avatar` 欄讀取）
- ✅ 歷史專區改成「年份分組卡片」
- ✅ Footer 動態年份
- ✅ 期刊論文數量自動計算（hero + about 兩處顯示為 `{n}+`）
- ✅ Publications 加 `article_type` 徽章（original / review / book / letter / case）
- ✅ 校友卡片顯示 `since` 年份
- ✅ About → 學術連結加入「實驗室內部網站」連結（指向 `internal/`，目前 404）

### 內容管理系統（Google Sheets 整合）
- ✅ 6 個分頁：news / publications / highlights / history / members / projects
- ✅ Sheet ID：`1vsWJdaav2tyVIYdcPnlRNZ7Yu6dwVu6nNIpYTJkoikY`
- ✅ 試算表 → fetch CSV via gviz → 自動渲染
- ✅ 圖片管理：拖到 GitHub `images/` 資料夾，試算表填路徑

### 文件
- ✅ `SETUP.md` — 完整操作手冊（含所有 type/group/category 對照表）
- ✅ `data/*.csv` — 6 個 CSV 範本
- ✅ `images/README.md` — 圖片管理說明

## 🚧 進行中：實驗室內部網站

**狀態：** 規劃階段，尚未實作

**需求：**
- 私密內部資源（採購申請、共用文件、儀器預約等）
- 必須有真正的登入機制（學生只能看不能改）
- 學生離開後可以撤銷權限

**已做的調研（mockups/ 資料夾有視覺模擬）：**

| 方案 | 工具 | 視覺 | 登入 | 設定成本 |
| ---- | ---- | ---- | ---- | -------- |
| **A/D** | Google Sites | Google 風格 | Google 帳號 | 5 分鐘 |
| **C** | Cloudflare Pages + Access | 完全自訂（沿用主站風） | Email OTP / Google SSO | 20 分鐘 |
| **B** | Notion 私人 workspace | Notion 風格 | Notion 帳號 | 10 分鐘 |

**模擬檔案：**
- `mockups/option-D-google-sites.html` — Google Sites 風格的內部站長相
- `mockups/option-C-cloudflare.html` — 自訂風格 + Cloudflare Access 登入畫面

**規劃中的 9 個內部功能（依重要性）：**

1. ⭐⭐⭐ 採購申請（Google Forms）
2. ⭐⭐⭐ 共用文件區（Google Drive）
3. ⭐⭐⭐ 儀器預約（Google Calendar）
4. ⭐⭐ 試劑/耗材庫存（Google Sheets 共編）
5. ⭐⭐ 緊急聯絡 / 安全須知（直接寫在內部站）
6. ⭐⭐ Paper Club 文獻清單（Sheets 或 Notion）
7. ⭐ 新生 Onboarding 流程（Google Doc）
8. ⭐ 實驗室會議紀錄（Google Drive）
9. ⭐ 投稿狀態追蹤（Google Sheets）

**下一步：** 使用者選擇方案後開始實作。

## 🗂 檔案結構

```
Virology-Lab/
├ index.html             ← 主站（單檔 HTML，1100+ 行）
├ data/
│ ├ news.csv             ← Google Sheets 範本
│ ├ publications.csv
│ ├ highlights.csv
│ ├ history.csv
│ ├ members.csv
│ └ projects.csv
├ images/
│ ├ README.md
│ └ profile.jpg          ← PI 大頭照（用戶上傳）
├ mockups/               ← 內部站視覺模擬（暫存）
│ ├ option-D-google-sites.html
│ └ option-C-cloudflare.html
├ SETUP.md               ← 給用戶的操作手冊
└ HANDOFF.md             ← 本文件（給下一次對話的 Claude）
```

## ⚠️ 已知技術細節

- 主站還保留註解掉的 `_LEGACY_DATA` 區塊（原本硬編碼資料），可考慮清掉但目前留著做備份
- Google Sheets 須設「知道連結的任何人 - 檢視者」 + 「發佈到網路」雙重設定
- gviz CSV 端點 `https://docs.google.com/spreadsheets/d/{ID}/gviz/tq?tqx=out:csv&sheet={NAME}`
- 圖片偏移調整參數：`object-position:center 20%`（CSS）
- Git 本地 user identity：`bole0918 <bole0918@gmail.com>`（已設於本 repo）

## 📋 給下一次對話的提示

對話開始時可以先問用戶：
1. 「上次討論到內部網站要選 A/D（Google Sites）還是 C（Cloudflare）？」
2. 「想先做哪幾個內部站功能？」

如果用戶想做別的事情（不是內部站），就跟著走就好。
