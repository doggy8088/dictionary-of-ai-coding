---
description: "駕馭與模型供應商之間的一次來回；駕馭送出脈絡，供應商回傳一個回應。"
---

從[駕馭](./Harness.md)到[模型供應商](./Model%20provider.md)的一次往返。駕馭發送當前[脈絡](./Context.md)；供應商回傳一個回應（一個[工具呼叫](./Tool%20call.md)或最終答案）。如果[代理人](./Agent.md)呼叫[工具](./Tool.md)，一條使用者訊息可能觸發許多次模型供應商請求——每個[工具結果](./Tool%20result.md)都會觸發另一次請求。

_情境例句：_

「一個問題燒了四萬個[詞元](./Token.md)？」
"One question burned forty thousand [tokens](./Token.md)?"

「看看工具呼叫——十二次 grep、八次讀取、四次編輯。每個工具結果都會觸發另一次模型供應商請求，而整個[工作階段](./Session.md)的前綴每次都要重新發送。」
"Look at the tool calls — twelve grep, eight read, four edits. Each tool result spawns another model provider request, and the whole [session](./Session.md) prefix re-sends every time."
