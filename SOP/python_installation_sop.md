# Python 安裝 SOP

## 1. 簡介
本SOP旨在提供在Windows 11環境下安裝Python的詳細步驟，並簡要說明macOS的安裝方式。Python是一種廣泛使用的高階程式語言，適用於網頁開發、數據分析、人工智慧等多種應用。

## 2. Windows 11 安裝

### 步驟 1: 前往 Python 官方下載頁面
開啟您的網頁瀏覽器，並前往 [Python 官方下載頁面](https://www.python.org/downloads/)。

### 步驟 2: 下載 Python 安裝程式
在頁面中，您會看到一個顯眼的「Download Python 3.14.0」按鈕。點擊此按鈕以下載適用於Windows的安裝程式。
![Python Download Button](python_downloads_page.png)
*（圖示為Python下載頁面，紅色框線處為下載按鈕）*

### 步驟 3: 執行安裝程式
1.  找到下載的 `.exe` 安裝檔案並執行。
2.  **重要：** 在安裝精靈的第一個畫面，請務必勾選「**Add Python X.Y to PATH**」（將Python X.Y加入環境變數）。這將允許您在命令提示字元中直接執行Python。
3.  選擇「Install Now」進行預設安裝，或選擇「Customize installation」進行自訂安裝（建議初學者使用預設安裝）。
4.  等待安裝完成。

### 步驟 4: 驗證安裝
1.  開啟「命令提示字元」（Command Prompt）。您可以按下 `Win + R`，輸入 `cmd`，然後按下 `Enter`。
2.  在命令提示字元中輸入以下指令並按下 `Enter`：
    ```bash
    python --version
    ```
3.  如果安裝成功，您將看到類似 `Python 3.14.0` 的版本資訊。

## 3. macOS 安裝

### 步驟 1: 前往 Python 官方下載頁面
與Windows相同，前往 [Python 官方下載頁面](https://www.python.org/downloads/)。

### 步驟 2: 下載 macOS 安裝程式
在頁面中找到「macOS」相關的下載連結（通常在「Looking for Python with a different OS?」下方）。點擊下載 `.pkg` 檔案。

### 步驟 3: 執行安裝程式
1.  找到下載的 `.pkg` 安裝檔案並執行。
2.  按照安裝精靈的指示完成安裝。

### 步驟 4: 驗證安裝
1.  開啟「終端機」（Terminal）。
2.  在終端機中輸入以下指令並按下 `Enter`：
    ```bash
    python3 --version
    ```
3.  如果安裝成功，您將看到類似 `Python 3.14.0` 的版本資訊。
