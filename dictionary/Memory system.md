一套試圖讓[代理人](./Agent.md)能夠跨[工作階段](./Session.md)[保有狀態](./Stateful.md)（Stateful）的系統。在工作階段進行中將資訊持久化到[環境](./Environment.md)，並在未來工作階段開始時重新載入[上下文視窗](./Context%20window.md)，使代理人在使用者[清除](./Clearing.md)工作階段後仍能維持連續性。

*情境例句：*

「我每次都要重新告訴它我用的是 Postgres，不是 MySQL。」
"I keep having to re-tell it I'm on Postgres, not MySQL."

「接上記憶系統——在第一個[對話輪次](./Turn.md)把它學到的內容寫入[檔案系統](./Filesystem.md)，並在工作階段開始時重新載入。[模型](./Model.md)本身是[無狀態的](./Stateless.md)；記憶層模擬了持續性。」
"Wire up a memory system — write what it learns to the [filesystem](./Filesystem.md) on the first [turn](./Turn.md), reload it at session start. The [model](./Model.md) itself is [stateless](./Stateless.md); the memory layer fakes continuity."
