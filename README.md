# 新搜尋分頁（Brave / Startpage）

這是一個簡單的自訂「新分頁／搜尋分頁」網頁範本，設計給 Brave 或其他 Chromium 系列瀏覽器做為自訂新分頁或靜態首頁使用。頁面以 Startpage 搜尋為預設搜尋引擎，並包含一個顯示風向與氣壓的簡易天氣卡片。

主要檔案

- `index.html` — 主頁面，包含 UI、樣式與小型的 JavaScript（載入 `weather.json`）。
- 圖片檔案 — 背景與前景圖片 (repo 中以 webp 檔案存在)。
- `weather.json` — 預期由使用者/系統放置的天氣資料 JSON（範例結構見下方）。

功能說明

- 以 Startpage 搜尋為預設，輸入文字按 Enter 會導向 Startpage 的搜尋結果（並帶上 segment 參數以示來源）。
- 顯示目前地點（由 `weather.json` 提供）、風向（度數 + 方位）與氣壓（hPa），並以簡單的圖像表示（指南針、氣壓儀）。
- 響應式設計：在窄螢幕/手機上會調整大小與位置以便閱讀與操作。

如何在本機預覽

1. 先把專案 clone 到本機：

   git clone https://github.com/czw313131/brave-browser-sear-hopa-peon.git

2. 進入資料夾並啟動簡易 HTTP 伺服器（以 Python 為例）：

   cd brave-browser-sear-hopa-peon
   python3 -m http.server 8000

3. 在瀏覽器開啟：

   http://localhost:8000/index.html

為什麼要用 HTTP（而不是直接開啟檔案）？

部分瀏覽器對於 local file 協定有 fetch/cors 的限制，使用 HTTP 伺服器可確保 index.html 能正確載入 `weather.json` 與其他資源。

weather.json 範例

請放置一個 JSON 檔案（檔名為 `weather.json`）與 `index.html` 同一目錄，結構如下：

{
  "location": "Taipei, TW",
  "wind_direction_10m": 135,
  "surface_pressure": 1013.2
}

- `location`：要顯示的地點字串。
- `wind_direction_10m`：風向（度數，0–359）。
- `surface_pressure`：氣壓，單位 hPa（浮點數）。

自訂與延伸

- 可將搜尋目標由 Startpage 改為其他搜尋引擎，修改 `index.html` 中的搜尋 URL 即可。
- 天氣來源目前採用靜態 `weather.json`：可串接外部氣象 API，或在本機產生動態 JSON 以符合頁面格式。
- 可根據需要加入溫度、降雨機率或更多圖示與動畫。

授權與貢獻

歡迎提出 issue 或 pull request。請在提 PR 時附上變更說明與預覽截圖。

本專案採用 MIT 授權（如需其他授權請提出）。

聲明

頁面使用的圖片與資源請注意版權與來源，若使用第三方圖像，請在專案中補上適當的授權與註明。
