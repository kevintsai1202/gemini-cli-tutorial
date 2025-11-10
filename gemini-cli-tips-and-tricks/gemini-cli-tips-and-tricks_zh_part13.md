## 技巧 23：使用 SETTINGS.JSON 自訂 GEMINI CLI

**快速用例：** 透過編輯 `settings.json` 設定檔，根據您的偏好或專案約定調整 CLI 的行為和外觀，而不是堅持一刀切的預設值。這讓您可以在所有會話中強制執行主題、工具使用規則或編輯器模式等內容。

Gemini CLI 具有高度可配置性。在您的主目錄 (`~/.gemini/`) 或專案資料夾（儲存庫中的 `.gemini/`）中，您可以建立一個 `settings.json` 檔案來覆蓋預設設定。CLI 的幾乎每個方面都可以在這裡進行調整——從視覺主題到工具權限。CLI 合併來自多個層級的設定：系統範圍的預設值、您的用戶設定和專案特定設定（專案設定會覆蓋用戶設定）。例如，您可能對深色主題有全域偏好，但特定專案可能需要更嚴格的工具沙盒；您可以透過每個層級的不同 `settings.json` 檔案來處理此問題。

在 `settings.json` 內部，選項以 JSON 鍵值對的形式指定。以下是一個程式碼片段，說明了一些有用的自訂：

```json
{
“theme”: “GitHub”,
“autoAccept”: false,
“vimMode”: true,
“sandbox”: “docker”,
“includeDirectories”: [”../shared-library”, “~/common-utils”],
“usageStatisticsEnabled”: true
}
```

在此範例中，我們將主題設定為「GitHub」（一種流行的配色方案），禁用 `autoAccept`（因此 CLI 在運行可能更改工具之前總是會詢問），為輸入編輯器啟用 Vim 鍵盤綁定，並強制使用 Docker 進行工具沙盒。我們還將一些目錄新增到工作區上下文 (`includeDirectories`)，以便 Gemini 預設可以看到共享路徑中的程式碼。最後，我們將 `usageStatisticsEnabled` 保持為 true 以收集基本使用統計資料（如果啟用，這會饋送到遙測中）。還有更多可用的設定——例如定義自訂顏色主題、調整 token 限制或將特定工具列入白名單/黑名單——所有這些都在配置指南中進行了說明。透過調整這些設定，您可以確保 Gemini CLI 為您的工作流程最佳地運行（例如，一些開發人員總是希望 `vimMode` 啟用以提高效率，而另一些開發人員可能更喜歡預設編輯器）。

編輯設定的一種便捷方式是透過內建的設定 UI。在 Gemini CLI 中運行命令 `/settings`，它將開啟一個互動式編輯器來配置您的設定。此介面允許您瀏覽和搜尋帶有描述的設定，並透過驗證輸入來防止 JSON 語法錯誤。您可以透過友好的選單調整顏色、切換 yolo（自動批准）等功能、調整檢查點（檔案儲存/恢復行為）等。更改會儲存到您的 `settings.json` 中，有些會立即生效（其他可能需要重新啟動 CLI）。

**專業技巧：** 為不同的需求維護單獨的專案特定 `settings.json` 檔案。例如，在團隊專案中，您可能會設定 `“sandbox”: “docker”` 和 `“excludeTools”: [”run_shell_command”]` 以鎖定危險操作，而您的個人專案可能允許直接 shell 命令。Gemini CLI 將自動從您的專案目錄樹中最近的 `.gemini/settings.json` 中提取並將其與您的全域 `~/.gemini/settings.json` 合併。此外，不要忘記您可以快速調整視覺偏好：嘗試 `/theme` 以互動方式切換主題而無需編輯檔案，這對於找到舒適的外觀非常有用。一旦找到一個，將其放入 `settings.json` 以使其永久化。

## 技巧 24：利用 IDE 整合 (VS CODE) 獲取上下文和差異

**快速用例：** 透過將 Gemini CLI 連結到 VS Code 來增強其功能——CLI 將自動知道您正在處理哪些檔案，甚至會在 VS Code 的差異編輯器中為您開啟 AI 建議的程式碼更改。這在 AI 助理和您的編碼工作區之間建立了一個無縫循環。

Gemini CLI 的強大功能之一是它與 Visual Studio Code 的 IDE 整合。透過在 VS Code 中安裝官方 Gemini CLI Companion 擴充功能並連接它，您可以讓 Gemini CLI 變得對您的編輯器「上下文感知」。這在實踐中意味著什麼？連接後，Gemini 知道您開啟的檔案、您目前的游標位置以及您在 VS Code 中選取的任何文字。所有這些資訊都會饋送到 AI 的上下文中。因此，如果您詢問「解釋此函數」，Gemini CLI 可以看到您突出顯示的確切函數並給出相關答案，而無需您將程式碼複製貼上到提示中。該整合最多共享您最近開啟的 10 個檔案，以及選取和游標資訊，讓模型對您的工作區有豐富的理解。

另一個巨大的好處是程式碼更改的原生差異比較。當 Gemini CLI 建議修改您的程式碼時（例如，「重構此函數」並產生一個補丁），它可以自動在 VS Code 的差異檢視器中開啟這些更改。您將在 VS Code 中看到並排的差異，顯示建議的編輯。然後，您可以使用 VS Code 熟悉的介面來審查更改，進行任何手動調整，甚至一鍵接受補丁。CLI 和編輯器保持同步——如果您在 VS Code 中接受差異，Gemini CLI 會知道並繼續會話，並應用這些更改。這種緊密的循環意味著您不再需要將程式碼從終端機複製到編輯器；AI 的建議直接流入您的開發環境。

**如何設定：** 如果您在 VS Code 的整合終端機中啟動 Gemini CLI，它將偵測到 VS Code，並通常會提示您自動安裝/連接擴充功能。您可以同意，它將運行必要的 `/ide install` 步驟。如果您沒有看到提示（或者您稍後啟用它），只需開啟 Gemini CLI 並運行命令：`/ide install`。這將為您擷取並安裝「Gemini CLI Companion」擴充功能到 VS Code 中。接下來，運行 `/ide enable` 以建立連接——CLI 將指示它已連結到 VS Code。您可以隨時使用 `/ide status` 進行驗證，它將顯示是否已連接並列出正在追蹤的編輯器和檔案。從那時起，Gemini CLI 將自動從 VS Code 接收上下文（開啟的檔案、選取範圍），並在需要時在 VS Code 中開啟差異。它本質上將 Gemini CLI 轉變為一個 AI 結對程式設計師，它存在於您的終端機中，但對您的 IDE 具有充分的感知。

目前，VS Code 是此整合主要支援的編輯器。（其他支援 VS Code 擴充功能的編輯器，例如 VSCodium 或一些 JetBrains 透過外掛，可能透過相同的擴充功能工作，但目前官方支援的是 VS Code。）然而，設計是開放的——有一個 IDE Companion Spec 用於開發與其他編輯器類似的整合。因此，將來我們可能會看到對 IntelliJ 或 Vim 等 IDE 的一流支援，透過社群擴充功能。

**專業技巧：** 連接後，您可以使用 VS Code 的命令面板來控制 Gemini CLI，而無需離開編輯器。例如，按下 `Ctrl+Shift+P`（Mac 上為 `Cmd+Shift+P`）並嘗試諸如「Gemini CLI：運行」（在終端機中啟動新的 CLI 會話）、「Gemini CLI：接受差異」（批准並應用開啟的差異）或「Gemini CLI：關閉差異編輯器」（拒絕更改）等命令。這些快捷鍵可以進一步簡化您的工作流程。請記住，您不總是需要手動啟動 CLI——如果您啟用整合，Gemini CLI 本質上會成為 VS Code 內部的一個 AI 協同開發人員，監控上下文並隨時準備在您處理程式碼時提供幫助。
