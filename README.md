# 大獅園群島 LION ISLES — 臺師大 3D 互動島嶼地圖

用 3D 低多邊形群島介紹國立臺灣師範大學。中央是百年本島，六座主題島用木棧橋串起來：百年亮點、研究亮點、社會貢獻 USR、永續發展、未來展望、師生榮耀，另有公館、林口兩座校區小島。設計手感參考沈伯洋「HEART 政策島」（https://puma.taipei/heart-island）。

## 資料來源

全部內容整理自臺師大官網 https://www.ntnu.edu.tw/ 和它的官方子網站（數位校史館、校務概況、研究亮點、USR、永續發展中心、校務發展計畫、校長的話、師大新聞），擷取日期 2026-10-28。每一條亮點都附原始連結，完整清單在網站右側「資料來源」分頁，以及 `site/js/data.js`。

## 怎麼跑

純靜態網站，Three.js 從 jsDelivr CDN 載入，不需要安裝任何套件。因為用了 ES modules，必須透過本機伺服器開啟：

```bash
python3 -m http.server 8791 --directory site
```

然後打開 http://localhost:8791 。

線上版：https://purduephoebe.github.io/ntnu-island/ （GitHub Pages，repo `purduephoebe/purduephoebe.github.io` 的 `ntnu-island/` 資料夾）。要更新，把 `site/` 的內容同步到那個資料夾再 push。

## 檔案

- `site/index.html`：頁面骨架和 UI
- `site/css/style.css`：樣式，包含夜間主題與手機版 bottom sheet
- `site/js/main.js`：3D 場景，包括島嶼建模、動畫、相機飛行、點選、時段切換、導覽和搜尋
- `site/js/data.js`：所有文字內容與來源連結。**要改內容只需要改這個檔**

## 功能

- 拖曳旋轉、縮放；點島嶼或名牌後，相機飛過去並打開亮點卡片
- 清晨、正午、黃昏、夜晚四種時段（夜晚窗戶亮燈、燈塔光束旋轉）
- 自動導覽、環繞、鳥瞰、全景
- 樓層剖面：點進一座島，建築會一層層分開，看得到教室和走廊，並標上 RF／3F… 與示意標高；「剖面」按鈕可一次展開全部建築
- 漫遊：按「漫遊」變成一位學生，用 WASD／方向鍵在各島和木棧橋之間走動，拖曳看四周、Shift 跑步、V 切換第一／第三人稱、E 看所在島的亮點、Esc 離開；手機版有螢幕方向鍵
- 跨主題關鍵字搜尋；網址 hash 可直接連到單一島嶼（例如 `#sustain`）
- 手機版：清單和卡片改成 bottom sheet

## 目前狀態

v1 完成（2026-10-28），2026-10-30 加入漫遊模式並公開發布到 GitHub Pages；桌機與手機版都在瀏覽器實測過。這是非官方展示作品。
