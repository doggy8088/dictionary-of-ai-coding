---
description: "模型實際做的事：從脈絡抽樣下一個詞元、附加上去，然後重複；這是它唯一的運作模式。"
---

[模型](./Model.md)實際上做的事。給定一個[脈絡](./Context.md)，它抽樣出下一個[詞元](./Token.md)，將其附加上去，然後再執行一遍。所有輸出——一個句子、一個[工具呼叫](./Tool%20call.md)、一個上千行的檔案——都是逐個詞元建構起來的。模型沒有其他運作模式。

_情境例句：_

「[代理人](./Agent.md)是怎麼『決定』要呼叫一個工具的？」
"How does the [agent](./Agent.md) 'decide' to call a tool?"

「它不是『決定』——一路到底都是下一個詞元預測（Next-Token Prediction）。工具呼叫不過是[駕馭](./Harness.md)從輸出串流中解析出來的一個結構化字串。」
"It doesn't — it's next-token prediction all the way down. The tool call is just a structured string the [harness](./Harness.md) parses out of the output stream."
