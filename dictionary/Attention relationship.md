在預測每個[詞元](./Token.md)時，[模型](./Model.md)會將[脈絡](./Context.md)中所有其他詞元都納入考量——有些影響深遠，有些幾乎微不足道。兩個詞元之間的配對關係即為**注意力關係**（Attention Relationship），有意義的配對（例如「她」與「Sarah」，或一個 `getUser()` 呼叫與其 `function getUser` 定義）彼此的影響遠大於無關聯的配對。一個包含 N 個詞元的脈絡，大約有 N² 個注意力關係。

*情境例句：*

「它一直在 diff 裡搞混那兩個 `user` 符號——聽起來像是進了[混沌區](./Smart%20zone.md)。」
"It keeps confusing the two `user` symbols across the diff — sounds like we're in the [dumb zone](./Smart%20zone.md)."

「對，每個呼叫端與其宣告之間的注意力關係互相干擾——相同的詞元形狀，但綁定的對象不同。把其中一個改名，配對關係就會變得清晰。」
"Yeah, the attention relationship between each call site and its declaration is fighting the other one — same token shape, different bindings. Rename one and the pairings sharpen."
