一條使用者訊息，加上[代理人](./Agent.md)在回應中所做的一切，直到它將控制權還給使用者為止。包含一次或多次[模型供應商請求](./Model%20provider%20request.md)——如果代理人呼叫[工具](./Tool.md)，則可能包含許多次。一個澄清問題結束這個輪次；你的回覆開始下一個。層級關係是[工作階段](./Session.md) **> 對話輪次（Turn）> 模型供應商請求**。

*情境例句：*

「一個輪次花了兩分鐘？」
"One turn took two minutes?"

「它在那個輪次裡發出了十四次[工具呼叫](./Tool%20call.md)——每次都是一個獨立的模型供應商請求。延遲不斷疊加，直到代理人最終把控制權還給你。」
"It made fourteen [tool calls](./Tool%20call.md) inside that turn — each one is a separate model provider request. Latency stacks up before the agent finally yields back to you."
