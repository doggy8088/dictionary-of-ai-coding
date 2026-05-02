[代理人模式](./Agent%20mode.md)（Agent Mode）中負責權限把關的切片——哪些[工具呼叫](./Tool%20call.md)會觸發[權限請求](./Permission%20request.md)（Permission Request），哪些會自動執行。這是模式系統的原始用途，後來[駕馭](./Harness.md)才開始在其上捆綁行為指令。

*情境例句：*

「它每次 grep 都暫停——[AFK](./AFK.md) 執行完全被卡死了。」
"It paused on every grep — totally killed the [AFK](./AFK.md) run."

「放寬唯讀[工具](./Tool.md)的權限模式，保留對寫入和 shell 操作的提示。研究型[工作階段](./Session.md)裡大多數的權限請求都是雜訊。」
"Loosen the permission mode for read-only [tools](./Tool.md), keep prompting on writes and shell. Most permission requests on a research [session](./Session.md) are noise."
