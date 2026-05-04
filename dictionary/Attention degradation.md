---
description: "工作階段變長時，每個詞元的注意力預算會分散到更多競爭者，重要關係的訊號因此變弱。"
---

隨著[工作階段](./Session.md)不斷增長，每個[詞元](./Token.md)的[注意力預算](./Attention%20budget.md)（Attention Budget）必須分配給更多的競爭者。任何一個[有意義關係](./Attention%20relationship.md)（Attention Relationship）上的訊號都會減弱；不相關的[脈絡](./Context.md)雜訊大量湧入。同樣的[模型](./Model.md)、同樣的[參數](./Parameters.md)——只是要從同一個盤子上餵食的嘴巴多了。這是清晰區與[混沌區效應](./Smart%20zone.md)的根本成因。

_情境例句：_

「它深陷混沌區了——憑空捏造出型別檔裡根本不存在的泛型。」
"It's deep in the dumb zone — inventing generics that aren't in the type file."

「注意力衰退（Attention Degradation）。型別定義仍在脈絡中，但它的訊號被我們後來加入的所有內容淹沒了。[清除](./Clearing.md)並重新載入。」
"Attention degradation. The type definitions are still in context, but the signal on them is buried under everything we've added since. [Clear](./Clearing.md) and reload."
