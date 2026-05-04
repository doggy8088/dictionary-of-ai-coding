---
description: "駕馭執行工具呼叫後送回的內容，例如檔案內容、輸出或錯誤；是代理人看見環境的唯一窗口。"
---

[駕馭](./Harness.md)執行[工具呼叫](./Tool%20call.md)後回傳的內容——檔案內容、指令輸出、錯誤訊息。這是[代理人](./Agent.md)感知[環境](./Environment.md)的唯一窗口。在*下一次*[模型供應商請求](./Model%20provider%20request.md)中傳回[模型](./Model.md)，模型才能決定如何處理它。工具呼叫和工具結果是同一次交換的兩端，都發生在同一個[對話輪次](./Turn.md)之內。

_情境例句：_

「它在推論這個檔案的內容時，好像把它當成空的。」
"It's reasoning about the file like it's empty."

「工具結果回傳的是權限拒絕，不是檔案內容。模型只看到了錯誤字串——它沒有任何其他窗口可以看見這個檔案。」
"The tool result came back as a permission denial, not the contents. The model only saw the error string — it has no other window onto the file."
