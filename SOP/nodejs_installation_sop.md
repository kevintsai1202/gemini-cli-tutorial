# Node.js 安裝 SOP

## 1. 簡介
本SOP旨在提供在Windows 11環境下安裝Node.js的詳細步驟，並簡要說明macOS的安裝方式。Node.js是一個基於Chrome V8 JavaScript引擎的JavaScript執行環境，常用於開發高效能的網路應用程式和後端服務。

## 2. Windows 11 安裝

### 步驟 1: 前往 Node.js 官方下載頁面
開啟您的網頁瀏覽器，並前往 [Node.js 官方下載頁面](https://nodejs.org/en/download/)。

### 步驟 2: 下載 Node.js 安裝程式
在頁面中，建議選擇「LTS (Long Term Support)」版本，因為它提供長期穩定支援。點擊對應Windows的下載連結（通常是 `.msi` 檔案）。
![Node.js Download Page](nodejs_downloads_page.png)
*（圖示為Node.js下載頁面，請選擇LTS版本的Windows安裝程式）*

### 步驟 3: 執行安裝程式
1.  找到下載的 `.msi` 安裝檔案並執行。
2.  按照安裝精靈的指示進行。通常，您可以接受所有預設選項，因為它會自動安裝 npm (Node Package Manager) 並將Node.js加入系統的 PATH 環境變數中。
3.  等待安裝完成。

### 步驟 4: 驗證安裝
1.  開啟「命令提示字元」（Command Prompt）。您可以按下 `Win + R`，輸入 `cmd`，然後按下 `Enter`。
2.  在命令提示字元中輸入以下指令並按下 `Enter`：
    ```bash
    node -v
    ```
3.  您將看到已安裝的 Node.js 版本號（例如：`v22.21.0`）。
4.  接著，輸入以下指令驗證 npm 是否也成功安裝：
    ```bash
    npm -v
    ```
5.  您將看到已安裝的 npm 版本號。

## 3. macOS 安裝

### 方式一: 使用官方安裝程式
1.  前往 [Node.js 官方下載頁面](https://nodejs.org/en/download/)。
2.  選擇「LTS (Long Term Support)」版本，點擊對應macOS的下載連結（通常是 `.pkg` 檔案）。
3.  找到下載的 `.pkg` 安裝檔案並執行，按照指示完成安裝。

### 方式二: 使用 Homebrew (推薦)
如果您已安裝 Homebrew (macOS 的套件管理器)，可以使用以下指令安裝 Node.js：
1.  開啟「終端機」（Terminal）。
2.  輸入以下指令並按下 `Enter`：
    ```bash
    brew install node
    ```

### 驗證安裝
1.  開啟「終端機」（Terminal）。
2.  輸入以下指令並按下 `Enter`：
    ```bash
    node -v
    ```
3.  您將看到已安裝的 Node.js 版本號。
4.  接著，輸入以下指令驗證 npm 是否也成功安裝：
    ```bash
    npm -v
    ```
5.  您將看到已安裝的 npm 版本號。