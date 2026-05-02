模型在每次[模型供應商請求](./Model%20provider%20request.md)（Model Provider Request）中所能看到的全部內容。容量有限、因模型而異，且是*模型感知任何事物的唯一介面*。

*避免使用：*「記憶體」——上下文視窗是工作狀態，不會跨[工作階段](./Session.md)持久保存。[記憶體](./Memory%20system.md)（Memory）是一個獨立概念，架構在其上層。

*情境例句：*

「我可以把整個 monorepo 貼到提示詞裡嗎？」
"Can I just paste the whole monorepo into the prompt?"

「上下文視窗有 20 萬個[詞元](./Token.md)——大概只是整個代碼庫的五分之一。選取任務會觸及的檔案，把其餘的留在[工具呼叫](./Tool%20call.md)後面按需載入。」
"The context window's 200k [tokens](./Token.md) — that's maybe a fifth of the repo. Pick the files the task touches, leave the rest behind a [tool call](./Tool%20call.md)."
