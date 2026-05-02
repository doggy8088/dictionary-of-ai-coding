由一個[代理人](./Agent.md)審查另一個代理人的工作，通常使用不同的[模型](./Model.md)或[系統提示詞](./System%20prompt.md)。非確定性的：它會形成判斷。可以在任何地方執行——合併前的 PR 審查、提交歷史的事後審查、作為[子代理人](./Subagent.md)在工作階段中途執行。CI 裡的 LLM-as-judge（語言模型作為裁判）是自動化審查，而非[自動化檢查](./Automated%20check.md)；判斷一件事屬於哪個類別，看的是斷言*做了什麼*，而非在哪裡執行。

*避免使用：*「AI 審查」、「代理人審查」——過於模糊，無法與執行工作的代理人本身區分。

*情境例句：*

「[AFK](./AFK.md) 執行產出了太多劣質 PR。」
"We're getting too many bad PRs from the [AFK](./AFK.md) runs."

「在合併前加一個自動化審查步驟——使用不同模型、獨立的系統提示詞，範圍鎖定在安全性和介面合約的變更。」
"Add an automated review step before merge — different model, separate system prompt, scoped to security and contract changes."
