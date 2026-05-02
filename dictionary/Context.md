[代理人](./Agent.md)目前可以存取的相關資訊。這是一個抽象名詞——不是模型看到的原始輸入（那是[上下文視窗](./Context%20window.md)），也不是持續累積的對話歷史（那是[工作階段](./Session.md)），而是*代理人當下對任務而言切實可用的知識*。「將某樣東西載入脈絡」意味著把它納入這個集合；「脈絡工程」（Context Engineering）是策劃和管理這個集合的學問。

*情境例句：*

「它不斷捏造型別裡根本不存在的欄位。」
"It keeps inventing fields that aren't in the type."

「型別檔沒有進脈絡——它在讀呼叫端然後猜。先把定義讀進來。」
"The type file isn't in context — it's reading the call sites and guessing. Read the definition in first."
