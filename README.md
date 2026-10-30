# 百年和平 HEPING 100 — 臺師大和平校區 3D 空拍地圖

（2026-10-30 前名為「大獅園群島 LION ISLES」，原始碼 repo 仍沿用舊名 `ntnu-lion-isles`。）

用 3D 低多邊形的空拍視角介紹國立臺灣師範大學和平校區：和平東路一段南邊是校本部，對面東北方是圖書館校區。六個主題分布在實際的建物上：百年亮點（行政大樓、普字樓、禮堂、文薈廳）、研究亮點（圖書館一帶）、社會貢獻 USR（教育學院大樓、羅馬廣場）、永續發展（文學院大樓、日光大道）、未來展望（科技與工程學院一帶）、師生榮耀（運動場、體育館）。建築位置依總務處的和平校區配置圖（https://www.ga.ntnu.edu.tw/ntnu_map/ ），方位與兩個校區的相對位置、比例以 Google 地圖衛星圖校正。設計手感參考沈伯洋「HEART 政策島」（https://puma.taipei/heart-island）。

## 資料來源

全部內容整理自臺師大官網 https://www.ntnu.edu.tw/ 和它的官方子網站（數位校史館、校務概況、研究亮點、USR、永續發展中心、校務發展計畫、校長的話、師大新聞），擷取日期 2026-10-28。每一條亮點都附原始連結，完整清單在網站右側「資料來源」分頁，以及 `site/js/data.js`。

## 怎麼跑

純靜態網站，Three.js 從 jsDelivr CDN 載入，不需要安裝任何套件。因為用了 ES modules，必須透過本機伺服器開啟：

```bash
python3 -m http.server 8791 --directory site
```

然後打開 http://localhost:8791 。

線上版：https://purduephoebe.github.io/ntnu-island/ ；原始碼：https://github.com/purduephoebe/ntnu-lion-isles 。線上版（GitHub Pages，repo `purduephoebe/purduephoebe.github.io` 的 `ntnu-island/` 資料夾）。要更新，把 `site/` 的內容同步到那個資料夾再 push。

## 檔案

- `site/index.html`：頁面骨架和 UI
- `site/css/style.css`：樣式，包含夜間主題與手機版 bottom sheet
- `site/js/main.js`：3D 場景，包括校園配置與建模、車流、動畫、相機飛行、點選、時段切換、導覽和搜尋
- `site/img/ntnu-emblem-red.png`：校徽（師大紅），取自臺師大形象識別系統
- `site/js/data.js`：所有文字內容與來源連結。**要改內容只需要改這個檔**

## 功能

- 拖曳旋轉、縮放；點建築或名牌後，相機飛過去並打開亮點卡片
- 清晨、正午、黃昏、夜晚四種時段（夜晚窗戶和路燈亮起）
- 自動導覽、環繞、鳥瞰、全景
- 樓層剖面：點進一個主題區，建築會一層層分開，看得到教室和走廊，並標上 RF／3F… 與示意標高；「剖面」按鈕可一次展開全部建築
- 漫遊：按「漫遊」變成一位學生，用 WASD／方向鍵在校園和街道上走動，拖曳看四周、Shift 跑步、V 切換第一／第三人稱、E 看所在島的亮點、Esc 離開；手機版有螢幕方向鍵
- 跨主題關鍵字搜尋；網址 hash 可直接連到單一主題區（例如 `#sustain`）
- 手機版：清單和卡片改成 bottom sheet

## 目前狀態

v1 完成（2026-10-28），2026-10-30 加入漫遊模式並公開發布到 GitHub Pages；同日改版成和平校區空拍地圖（v=31 已上線），並依 Google 地圖衛星圖校正配置（v=32，尚未上線）；桌機與手機版都在瀏覽器實測過。這是非官方展示作品。
