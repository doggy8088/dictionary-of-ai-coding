---
description: "參數本身；無狀態，只做下一個詞元預測，無法單靠自己完成代理式工作。"
---

即[參數](./Parameters.md)（Parameters）本身。[無狀態](./Stateless.md)（Stateless）——執行[下一個詞元預測](./Next-token%20prediction.md)，僅此而已。「Claude Opus 4.7」和「GPT-5」都是模型。模型本身無法做任何代理人該做的事；它必須被[駕馭化](./Harness.md)（Harnessed）。

_情境例句：_

「規劃步驟要不要把模型從 Sonnet 換成 Opus？」
"Should we switch the model from Sonnet to Opus for the planning step?"

「試試看吧——但這個任務大部分工作是駕馭在做。如果[系統提示詞](./System%20prompt.md)和[工具](./Tool.md)設定不對，換模型也沒用。」
"Try it — but the harness is doing most of the lifting on this task. The model swap won't help if the [system prompt](./System%20prompt.md) and [tools](./Tool.md) are wrong."
