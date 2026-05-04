---
description: "模型輸出的工具名稱與引數，只是結構化文字；駕馭必須讀取並執行。"
---

[模型](./Model.md)輸出的、指定某個[工具](./Tool.md)及其參數的內容——這不過是結構化文字。它本身不做任何事；[駕馭](./Harness.md)必須讀取它並執行。由模型在一次[模型供應商請求](./Model%20provider%20request.md)中產生。

_情境例句：_

「它說它跑了測試，但檔案的時間戳記沒有變。」
"It said it ran the tests but the file timestamps haven't changed."

「看一下對話紀錄——它是真的發出了工具呼叫，還是只是描述跑了測試？模型產生呼叫指令，但如果駕馭沒有執行它，什麼都沒發生。」
"Look at the transcript — did it actually emit a tool call, or just describe running them? The model produces the call, but if the harness didn't execute it, nothing happened."
