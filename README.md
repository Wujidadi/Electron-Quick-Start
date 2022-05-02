# Electron Quick Start

Electron 快速入門簡易範例。

## 參考資料及注意事項
* 官方文件：[快速入门 | Electron](https://www.electronjs.org/zh/docs/latest/tutorial/quick-start)  
  快速入門原有的 [README.md](README.old.md)
* [Electron - 用網頁技術做一個桌面應用程式吧！ - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天](https://ithelp.ithome.com.tw/articles/10254357)  
  但這篇有 2 個問題需要注意：
  1. 官方推薦用 **electron-forge** 取代 **electron-builder** 來打包，而且前者比後者快得多，開發階段也不需要 codesign 就能編譯
  2. 從 `preload.js` 將 Node.js 及 Electron 需要的後端方法或變數傳給前端（`renderer.js`），用 `window.xxx` 是傳不過去的，必須改用 Electron 的 `contextBridge.exposeInMainWorld` 方法
* 開發階段以 **electron-reloader** 實現 hot reload：[How to set up hot reload on Electron](https://flaviocopes.com/electron-hot-reload/)
* 以 **electron-forge** 打包時，須注意以下 2 點：
  1. APP 圖示在 macOS 必須為 icns、在 Windows 必須為 ico 格式
  2. APP 顯示名稱與 Menu -> About 的顯示名稱不同，分別設定在 `package.json` 的 `config.forge.packagerConfig.name` 及 `productName`（最外層）
