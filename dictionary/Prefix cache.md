---
description: "供應商端的儲存機制，讓連續請求可跳過重複處理共同前綴，並以較低費率計費。"
---

[供應商](./Model%20provider.md)端的快取儲存區，讓連續的[模型供應商請求](./Model%20provider%20request.md)能夠跳過重新處理共享前綴的步驟。當一個請求的開頭與近期某個請求的開頭吻合——相同的[系統提示詞](./System%20prompt.md)、相同的歷史記錄到某個時間點——供應商就重複使用先前的運算結果，並以[快取詞元](./Cache%20tokens.md)（Cache Tokens）的折扣費率計費。

任何改變前綴的操作（重新排列檔案順序、在[工作階段](./Session.md)中途改寫系統提示詞、在頂部注入時間戳記）都會從該點起使快取失效，之後的請求以全額[輸入詞元](./Input%20tokens.md)費率計費。

_情境例句：_

「為什麼帳單在工作階段中途突然飆高？」
"Why did the bill spike halfway through the session?"

「[駕馭](./Harness.md)開始在每個[對話輪次](./Turn.md)把當前時間注入系統提示詞。前綴快取在第一個改變的詞元處就失效了，所以此後每次請求都以全額費率計費。」
"[Harness](./Harness.md) started injecting the current time into the system prompt every [turn](./Turn.md). Prefix cache breaks at the first changed token, so every request after that billed at full rate."
