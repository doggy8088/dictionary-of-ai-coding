同樣的輸入可能產生不同的輸出。用完全相同的[脈絡](./Context.md)跑同一個[模型](./Model.md)兩次，你可能會得到兩個不同答案——有時只差一個字，有時是完全不同的做法。你的程式碼不需要有任何改變，這件事也可能發生。

這是模型產生文字的方式，以及[模型供應商](./Model%20provider.md)如何處理[請求](./Model%20provider%20request.md)的特性。沒有哪個設定可以一鍵把它消掉。

你應該預期[代理](./Agent.md)在同一個任務上會產生一段結果分布。有些日子模型看起來很敏銳；有些日子它像是完全抓不到重點。同一個任務，不同次擲骰。

小心不要過度替這件事編故事。人類是會尋找模式的機器，一連串糟糕的執行結果，很容易讓人覺得「模型這週是不是變差了」。通常，那只是分布而已。

*情境例句：*

「Claude 今天爛透了。他們是不是發了一個更差的版本？」
"Claude has been awful today. Did they ship a worse version?"

「大概不是——模型輸出是非決定性的。同一個任務本來就會有好日子和壞日子。先明天再試一次，再開始找原因。」
"Probably not — model output is non-deterministic. You're going to have good days and bad days on the same task. Try again tomorrow before you go looking for a cause."
