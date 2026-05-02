# Upstream 自動更新翻譯策略

這份文件定義如何把 upstream 的新增與修改同步到本 repo，同時維持 zh-TW 譯文品質與產生檔一致性。

## 目標

- 追蹤 upstream 新增、修改、刪除或重新排序的 dictionary 條目。
- 將 upstream 的英文內容轉寫為自然、精準的繁體中文。
- 保留原始術語檔名與 `internal/Curriculum.md` 的英文條目名稱，避免破壞產生器與錨點。
- 只修改來源檔：`dictionary/*.md`、`internal/Curriculum.md`、`internal/README.template.md`。`README.md` 必須由 `npm run generate` 重新產生。

## 原則

1. 不直接 merge 或 cherry-pick upstream commit 到本地分支，除非該 commit 不含需翻譯內容。
2. 以 upstream diff 作為同步來源，再把內容套用成 zh-TW 版本。
3. `README.md` 是 generated file，不手改。
4. dictionary 條目檔名維持 upstream 英文術語，例如 `dictionary/Non-determinism.md`。
5. `internal/Curriculum.md` 的 bullet 維持英文術語；section 標題維持 zh-TW。
6. 條目內連到其他條目的連結只在第一次出現時加連結，後續同詞不重複連結。
7. 保留英文情境例句，並在前一行提供 zh-TW 翻譯。

## 標準流程

### 1. 更新 upstream 參考

```bash
git fetch upstream --quiet
git --no-pager rev-list --left-right --count HEAD...upstream/main
git --no-pager log --oneline HEAD..upstream/main
```

`rev-list` 的右側數字代表 upstream 比目前分支多出的 commit 數。若右側為 `0`，不需要同步。

### 2. 盤點 upstream 變更

```bash
git --no-pager show --stat --oneline HEAD..upstream/main
git --no-pager diff --name-status HEAD..upstream/main
```

依檔案類型分類：

| 檔案 | 處理方式 |
| --- | --- |
| `dictionary/*.md` | 讀 upstream 原文，新增或更新本地 zh-TW 譯文 |
| `internal/Curriculum.md` | 套用條目順序與新增/刪除項目，section 標題翻成 zh-TW |
| `internal/README.template.md` | 比對語意後翻譯模板文案 |
| `README.md` | 忽略 upstream diff，最後用產生器重建 |
| 其他檔案 | 判斷是否為工具、規則或專案結構變更；不需翻譯的可考慮 cherry-pick |

### 3. 讀取 upstream 原文

針對新增或修改的條目，用 `git show` 讀取 upstream 版本：

```bash
git --no-pager show upstream/main:'dictionary/Term.md'
git --no-pager show upstream/main:'internal/Curriculum.md'
```

不要從 `README.md` 抽內容，因為它是產生結果，可能混入錨點改寫與目錄。

### 4. 套用 zh-TW 內容

新增條目時：

1. 在 `dictionary/` 新增同名 `.md` 檔。
2. 翻譯正文為自然繁中，不逐字硬翻。
3. 第一次提到既有 dictionary 術語時，使用相對連結，例如 `[模型](./Model.md)`。
4. 同一條目中第二次以後出現同詞時，不再加連結。
5. 英文 usage/example 保留在 zh-TW 例句下一行。

更新既有條目時：

1. 先比對 upstream 英文差異。
2. 只改對應段落，不重寫整篇，避免無關 diff。
3. 若 upstream 調整定義邏輯，保留其語意結構，再翻成 zh-TW。

### 5. 更新 Curriculum

`internal/Curriculum.md` 是 dictionary 輸出順序的來源。同步時：

- 新增條目放在 upstream 指定位置。
- 刪除 upstream 移除的條目，但先確認本地沒有刻意保留的翻譯差異。
- 若 upstream section 標題改名，翻成 zh-TW 後更新。
- bullet 一律使用英文檔名基底，不翻譯。

### 6. 重新產生 README

```bash
npm run generate
```

若產生失敗，通常代表：

- `internal/Curriculum.md` 引用了不存在的 `dictionary/*.md`。
- `dictionary/` 有未列入 curriculum 的孤兒檔案。
- section heading 格式不符合 `## Section N — Title`。

### 7. 檢查結果

```bash
git --no-pager diff --check
git --no-pager diff --stat
git --no-pager status --short
```

必要時再檢查 README 內是否出現新條目：

```bash
rg -n "Term|翻譯關鍵詞" README.md internal/Curriculum.md dictionary
```

## 自動化建議

可以逐步加入一支同步輔助腳本，但不要讓腳本自動翻譯並直接覆寫檔案。建議自動化範圍如下：

1. `fetch-upstream`：執行 `git fetch upstream` 並列出 ahead/behind。
2. `list-upstream-changes`：輸出 `HEAD..upstream/main` 的 commit、檔案清單與 dictionary 條目清單。
3. `extract-upstream-entry`：把 upstream 原文輸出到暫存區或 stdout，供人工翻譯。
4. `validate-translation-sync`：確認 curriculum 與 dictionary 沒有缺漏，並執行 `npm run generate`、`git diff --check`。

不建議自動化的部分：

- 不讓機器直接決定術語譯名。
- 不自動覆蓋既有譯文。
- 不自動處理需要語意判斷的 section 標題或定義改寫。

## 術語一致性

新增或更新翻譯時，優先沿用 repo 既有譯法：

| English | zh-TW |
| --- | --- |
| model | 模型 |
| context | 脈絡 |
| context window | 上下文視窗 |
| token | 詞元 |
| agent | 代理 |
| tool call | 工具呼叫 |
| tool result | 工具結果 |
| session | 工作階段 |
| turn | 對話輪次 |
| hallucination | 幻覺 |
| failure mode | 失敗模式 |

若遇到新術語，先搜尋既有譯法：

```bash
rg -n "English term|可能的中文譯名" dictionary internal README.md
```

找不到時，選擇清楚、自然、可在技術討論中重複使用的譯名，並在第一次出現時可保留英文括號輔助理解。

## 衝突處理

- upstream 只新增條目：新增 zh-TW 條目並更新 curriculum。
- upstream 修改既有條目：比對段落後局部更新譯文。
- upstream 移除條目：同步移除前，確認本地沒有引用該條目的連結。
- upstream 改檔名：以新檔名建立譯文，更新所有連結與 curriculum，移除舊檔。
- upstream 修改產生器：先套用工具變更，再跑 `npm run generate` 確認輸出格式。

## 完成條件

一次 upstream 翻譯同步完成時，應滿足：

- upstream 新增或修改的 dictionary 語意都已反映為 zh-TW。
- `internal/Curriculum.md` 與 upstream 結構一致，但 section 標題使用 zh-TW。
- `README.md` 已重新產生。
- `git diff --check` 通過。
- `git status --short` 只顯示本次同步應有的檔案變更。
