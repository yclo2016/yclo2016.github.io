# AI Research Notes — 寫作與維護規則

這是 YC 的個人部落格（Jekyll + Chirpy 主題，部署在 GitHub Pages）。
內容是「研究筆記」與「手把手教學」，大多由 Claude 協助研究與撰寫。

## 語言

- 一律使用**繁體中文**（台灣用語），不要使用簡體中文。
- 專有名詞第一次出現時中英對照，例如「工作階段（Session）」，之後可只用中文或英文。
- 指令、檔名、按鈕名稱保持原文，用 `code` 標示；介面按鈕用**粗體**，例如 **Create PR**。

## 隱私（最重要）

這是**公開** repo，所有檔案和提交紀錄任何人都看得到。文章、設定檔、提交訊息中**不可以**出現：

- 密碼、API 金鑰、存取權杖（Token）、任何憑證
- 站長的個人資料：本名、Email、電話、住址、工作單位
- 站長電腦或帳號的詳細設定、私人對話內容

需要舉例時，使用本站公開的檔案（例如 `_config.yml`、`.github/workflows/`），或使用明顯的假資料（例如 `example.com`）。不確定能不能公開時，先問站長。

## 文章規則

- 放在 `_posts/`，檔名 `YYYY-MM-DD-英文-slug.md`。
- 分類（categories）只用兩個第一層：`[教學, ...]` 或 `[研究筆記, ...]`，第二層放主題，例如 `[教學, Claude Code]`。
- 標籤（tags）用英文小寫，例如 `claude-code`、`github-pages`。
- `date` 要帶時區且不可晚於現在時間，否則 Jekyll 不會產生該文章，例如 `2026-09-24 12:00:00 +0800`。
- 教學文必須：
  - 用**真實、有意義的例子**（最好就是本站或讀者真的會做的事），不要為了示範而編造的例子。
  - 每個步驟具體到可以照著做：去哪裡、點什麼、輸入什麼、預期看到什麼。
  - 在關鍵處加入「原來可以這麼想」的提示框，說明背後的思維轉換，而不只是操作。
  - 標註資料來源（官方文件連結）與撰寫日期；工具會更新，過時的地方要能被找出來。
- 可用 Chirpy 提示框：`{: .prompt-tip }`、`{: .prompt-info }`、`{: .prompt-warning }`、`{: .prompt-danger }`。
- 需要流程圖時在 front matter 加 `mermaid: true`。

## 建置與檢查

```bash
bundle install
bundle exec jekyll build        # 產生 _site/
bundle exec htmlproofer _site --disable-external --ignore-urls "/^http:\/\/127.0.0.1/,/^http:\/\/0.0.0.0/,/^http:\/\/localhost/"
```

推送前請先確認以上兩個指令都成功。GitHub Actions 會在 PR 上跑同樣的檢查，合併到 `main` 後自動部署。
