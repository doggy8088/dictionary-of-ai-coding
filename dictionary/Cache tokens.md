---
description: "供應商透過前綴快取從先前請求中快取的輸入詞元，計費通常低很多。"
---

[供應商](./Model%20provider.md)（Model Provider）從先前的[模型供應商請求](./Model%20provider%20request.md)（Model Provider Request）快取下來的[輸入詞元](./Input%20tokens.md)（Input Tokens），不必重新處理。當連續的請求共享同一個前綴時，供應商透過其[前綴快取](./Prefix%20cache.md)（Prefix Cache）重複使用先前的運算結果，並以大幅折扣的費率計費快取部分。這是讓長[工作階段](./Session.md)在成本上可行的關鍵機制——沒有它，每個[對話輪次](./Turn.md)都要重新支付整段歷史的費用。

_情境例句：_

「長工作階段的費用很驚人——一次重構花了八美元。」
"Cost on long sessions is brutal — eight bucks for a refactor."

「看看快取詞元（Cache Tokens）。如果[駕馭](./Harness.md)在輪次之間重新排列[系統提示詞](./System%20prompt.md)或檔案，前綴就會失效，每次請求都要以全額輸入詞元費率重新計費。」
"Check the cache tokens. If the [harness](./Harness.md) is reordering the [system prompt](./System%20prompt.md) or files between turns, the prefix breaks and you re-pay full input rate every request."
