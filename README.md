# 日序 DAYFLOW

日序是一款以日常規劃為主的行程與待辦管理網頁。它提供今日總覽、行程月曆與待辦時間線，並支援在桌面及手機瀏覽器中使用。

## 功能

- **今日總覽**：查看當日行程、待辦數量，以及已設定的提醒摘要。
- **行程月曆**：按月份瀏覽行程與未完成待辦的每日數量，並選擇日期查看內容。
- **待辦時間線**：依截止時間查看任務、標記完成狀態及編輯任務。
- **行程管理**：新增、編輯或刪除行程，設定日期、起訖時間、地點、備註與提醒時間。
- **待辦管理**：新增、編輯或刪除任務，設定截止日期與時間、優先順序、提醒時間及完成狀態。
- **帳號登入**：使用電子郵件與密碼建立帳號、登入及登出。
- **雲端同步**：登入後，行程與待辦會儲存在 Firestore 的個人資料路徑，可在其他裝置登入使用。
- **響應式介面**：依螢幕大小調整版面；手機畫面使用底部導覽列。

提醒目前以頁面上的摘要呈現，不會發送瀏覽器或系統通知。

## Firebase 與資料保存

- 使用 Firebase Authentication 的電子郵件／密碼登入。
- 行程與待辦儲存在 Cloud Firestore 的 `users/{uid}/data/dayflow` 文件中；Firestore 規則限制帳號只能存取自己的資料。
- 瀏覽器也會保留目前帳號的本機資料副本。第一次登入且雲端尚無資料時，會將舊版 `localStorage` 資料匯入帳號。
- 首次使用時會建立示範行程與待辦，方便體驗功能。

## 本機執行

在專案資料夾開啟 PowerShell，執行：

```powershell
py -m http.server 8000
```

接著在瀏覽器開啟 [http://localhost:8000/](http://localhost:8000/)。停止本機伺服器時，回到 PowerShell 按 `Ctrl+C`。

## 發布到 GitHub Pages

1. 將 `index.html`、`README.md` 和 `PRD.md` 上傳到 GitHub 儲存庫。
2. 在儲存庫開啟 **Settings → Pages**。
3. 在 **Build and deployment** 選擇 **Deploy from a branch**。
4. 選擇 `main` 分支與 `/(root)` 資料夾，然後按 **Save**。
5. 部署完成後，可在 Pages 設定頁查看網站網址。

首頁檔案請保留名稱 `index.html`，GitHub Pages 才會在儲存庫的網站根網址顯示此頁面。
部署後，請在 Firebase Authentication 的授權網域設定中加入 GitHub Pages 網域，才能從發布網站登入。

## 專案文件

- [產品需求文件（PRD）](PRD.md)
