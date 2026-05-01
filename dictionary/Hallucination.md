充滿自信卻又錯誤的[模型](./Model.md)輸出。分為兩種類型，各有不同的成因與修復方式：

- *事實性幻覺*（Factuality Hallucination）——捏造或錯誤的世界知識（一個不存在的函式、錯誤的 API 簽名、虛假的引用來源）。成因是[參數化知識](./Parametric%20knowledge.md)的缺口，常發生在[知識截止日期](./Knowledge%20cutoff.md)之後的內容。修復方式：載入正確的[情境知識](./Contextual%20knowledge.md)。
- *忠實性幻覺*（Faithfulness Hallucination）——輸出偏離了已載入的**情境知識**、使用者的指令，或模型自身先前的推理。這是[注意力衰退](./Attention%20degradation.md)（Attention Degradation）的症狀，在[混沌區](./Smart%20zone.md)會更嚴重。修復方式：[清除](./Clearing.md)或[壓縮摘要](./Compaction.md)。

*避免使用：*「幻覺」作為「錯誤」的代名詞——不指明是哪種類型，這個詞就沒有任何診斷價值。

*使用範例：*

「它幻覺出了 Schema 上一個 `parseAsync` 方法。」

「是事實性還是忠實性幻覺？」

「那個方法在我貼的文件裡有——它只是在第四十個[對話輪次](./Turn.md)後停止讀那份文件了。」

「那就是忠實性幻覺。壓縮摘要並重新載入，不用再加更多文件了。」
