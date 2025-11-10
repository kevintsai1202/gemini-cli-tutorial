## 入門

**安裝：** 您可以透過 npm 安裝 Gemini CLI。要進行全域安裝，請使用：

```pwsh
npm install -g @google/gemini-cli
```

或者使用 npx 運行它而無需安裝：

```pwsh
npx @google/gemini-cli
```

Gemini CLI 適用於所有主要平台（它使用 Node.js/TypeScript 構建）。安裝後，只需在終端機中運行 `gemini` 命令即可啟動互動式 CLI。

**身份驗證：** 首次使用時，您需要向 Gemini 服務進行身份驗證。您有兩個選項：(1) Google 帳戶登入（免費層級）——這讓您可以免費使用 Gemini 2.5 Pro，並享有慷慨的使用限制（大約每分鐘 60 個請求和每天 1,000 個請求）。啟動時，Gemini CLI 將提示您使用 Google 帳戶登入（無需付費）。(2) API 金鑰（付費或更高層級的存取）——您可以從 Google AI Studio 獲取 API 金鑰，並設定環境變數 `GEMINI_API_KEY` 以使用它。

API 金鑰的使用可以提供更高的配額和企業資料使用保護；提示不會用於付費/計費使用的訓練，但日誌可能會為了安全而保留。

例如，新增到您的 shell 設定檔：

```pwsh
$env:GEMINI_API_KEY=”YOUR_KEY_HERE”
```

**基本用法：** 要啟動互動式會話，只需運行不帶任何參數的 `gemini`。您將獲得一個 `gemini>` 提示符，您可以在其中輸入請求或命令。例如：

```pwsh
PS D:\> gemini
gemini> 使用 SQLite 建立一個 React 食譜管理應用程式
```

然後，您可以觀察 Gemini CLI 建立檔案、安裝依賴項、運行測試等，以滿足您的請求。如果您喜歡一次性調用（非互動式），請使用 `-p` 標誌和提示，例如：

```pwsh
gemini -p “總結所附檔案的要點。@./report.txt”
```

這將輸出單個回應並退出。您還可以將輸入管道傳輸到 Gemini CLI：例如，`echo “數到 10” | gemini` 將透過 stdin 傳送提示。

**CLI 介面：** Gemini CLI 提供了一個豐富的類似 REPL 的介面。它支援斜線命令（以 `/` 為字首的特殊命令，用於控制會話、工具和設定）和驚嘆號命令（以 `!` 為字首，用於直接執行 shell 命令）。我們將在下面的專業技巧中介紹其中許多。預設情況下，Gemini CLI 在安全模式下運行，任何修改您系統的操作（寫入檔案、運行 shell 命令等）都會要求確認。當提出工具操作時，您將看到差異或命令，並提示（Y/n）批准或拒絕它。這確保 AI 不會在未經您同意的情況下進行不必要的更改。
