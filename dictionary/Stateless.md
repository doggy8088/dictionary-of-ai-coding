不攜帶任何資訊向前傳遞。[模型](./Model.md)在[模型供應商請求](./Model%20provider%20request.md)（Model Provider Requests）之間是無狀態的——每次請求重新發送完整的[上下文視窗](./Context%20window.md)，因為模型無法看到其他任何東西。[代理人](./Agent.md)預設在[工作階段](./Session.md)之間是無狀態的：新工作階段從空白開始，沒有任何先前工作階段的痕跡。與[有狀態](./Stateful.md)（Stateful）相對。

*情境例句：*

「為什麼每次我[清除](./Clearing.md)之後它就忘記了那個慣例？」
"Why does it forget the convention every time I [clear](./Clearing.md)?"

「模型是無狀態的——新工作階段從空白開始。如果你想保留它，就把它寫入 [AGENTS.md](./AGENTS.md.md) 或一個[駕馭](./Harness.md)在工作階段開始時會載入的記憶檔案。」
"The model's stateless — the new session starts empty. If you want it carried, write it to [AGENTS.md](./AGENTS.md.md) or a memory file the [harness](./Harness.md) loads at session start."
