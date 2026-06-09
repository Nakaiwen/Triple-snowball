資產配置試算器 — PWA（可安裝、可離線）
=======================================

資料夾內容：
  index.html              主程式（已內嵌 PWA 設定與安裝鈕）
  manifest.webmanifest    App 資訊（名稱、圖示、顏色）
  sw.js                   Service Worker（離線快取）
  icons/                  App 圖示

【重要】PWA 必須透過 HTTPS（或 localhost）伺服器開啟才會生效。
直接用 file:// 雙擊 index.html 仍可試算，但「安裝為 App」與「離線使用」不會啟用
（瀏覽器規定 Service Worker 只能在 https 或 localhost 註冊）。

部署方式（擇一）：

A. GitHub Pages（最簡單，你已在用）
   1. 把整個資料夾的檔案放進 repo（保持相對路徑：icons/ 要跟著一起）。
   2. 開 Settings → Pages → 指定分支。
   3. 用 https://你的帳號.github.io/repo名/ 開啟。
   4. 手機 Chrome/Safari 開啟後，會出現「加入主畫面／安裝」；
      桌面 Chrome 網址列右側會出現安裝圖示，或按頁面上的「⬇ 安裝為 App」鈕。

B. 本機測試
   在這個資料夾執行： python3 -m http.server 8000
   然後瀏覽器開 http://localhost:8000/

更新版本：改了 index.html 後，把 sw.js 裡的 'asset-allocator-v1' 改成 v2，
使用者下次連線就會自動換到新版（舊快取會被清掉）。

iOS 注意：iPhone 要用「Safari」開 → 分享鈕 → 加入主畫面。
（iOS 不支援 beforeinstallprompt，所以不會出現頁面上的安裝鈕，要走分享選單。）
