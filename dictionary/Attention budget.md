---
description: "每個詞元能分配給其他脈絡的影響力有限；這是逐詞元的，不會隨脈絡變長而增加。"
---

每個[詞元](./Token.md)（Token）能分配給其餘[脈絡](./Context.md)（Context）的影響力是有限的。對[某個關係](./Attention%20relationship.md)（Attention Relationship）施加大量影響，留給其他關係的就越少。這個預算是每個詞元固定的，不會隨脈絡擴大而增長，這正是為何[工作階段](./Session.md)越長，效果越稀薄。

_情境例句：_

「它為什麼一直忽略我貼在最上面的 Schema？」
"Why does it keep ignoring the schema I pasted at the top?"

「我們已深入[混沌區](./Smart%20zone.md)了——每個詞元的注意力預算是固定的，但脈絡不斷增長。Schema 的訊號現在必須跟幾千個新詞元競爭。」
"We're well into the [dumb zone](./Smart%20zone.md) — every token's attention budget is fixed, but the context kept growing. The signal on the schema is now competing with thousands of newer tokens."
