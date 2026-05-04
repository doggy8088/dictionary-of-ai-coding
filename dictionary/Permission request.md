---
description: "駕馭在執行未預先核准的工具呼叫前顯示給使用者的內容，是把人放回流程中的機制。"
---

[駕馭](./Harness.md)在執行未預先核准的[工具呼叫](./Tool%20call.md)前，向使用者展示的提示。[模型](./Model.md)產生工具呼叫；駕馭不立即執行，而是暫停並詢問使用者。核准則執行；拒絕則駕馭將拒絕結果作為[工具結果](./Tool%20result.md)回報給模型。這是駕馭讓人類加入[迴圈](./Human-in-the-loop.md)以監督風險或敏感操作的機制。

_情境例句：_

「它被一個權限請求卡住十分鐘了——我開會去了。」
"It's been blocked on a permission request for ten minutes — I was in a meeting."

「這就是人在迴圈的代價。預先核准安全的[工具](./Tool.md)，讓請求只在真正有風險的操作上觸發。」
"That's the cost of human-in-the-loop. Pre-approve the safe [tools](./Tool.md) so the request only fires on the actually-risky calls."
