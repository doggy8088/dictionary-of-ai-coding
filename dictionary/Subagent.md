---
description: "由另一個代理人透過工具呼叫啟動的代理人；在自己的工作階段執行，回報單一工具結果，且不能再啟動子代理人。"
---

由另一個代理人透過[工具呼叫](./Tool%20call.md)（Tool Call）生成的[代理人](./Agent.md)。在自己的[工作階段](./Session.md)中、帶著自己的[上下文視窗](./Context%20window.md)運行，並回傳單一[工具結果](./Tool%20result.md)。與[交接](./Handoff.md)（Handoff）不同——父代理人明確期待一個返回結果；交接則沒有返回路徑。**無法再生成子代理人**——這個樹結構只有一層深。子代理人的存在是為了隔離[脈絡](./Context.md)，而非構建層級結構。

_情境例句：_

「grep 結果把我的脈絡撐爆了。」
"The grep results are blowing out my context."

「生成一個子代理人（Subagent）來做搜尋——它用自己的上下文視窗消耗那些雜訊，再把你真正需要的兩個檔案路徑回報給你。」
"Spawn a subagent to do the search — it'll burn its own context window on the noise and report back the two file paths you actually need."
