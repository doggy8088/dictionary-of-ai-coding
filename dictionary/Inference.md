---
description: "執行訓練好的模型來產生輸出；每次模型供應商請求都會發生，參數保持固定。"
---

執行已訓練好的[模型](./Model.md)以產生輸出——每次[模型供應商請求](./Model%20provider%20request.md)（Model Provider Request）都在做這件事。[參數](./Parameters.md)（Parameters）維持不變；模型只是對給定的[脈絡](./Context.md)進行[下一個詞元預測](./Next-token%20prediction.md)。相較於[訓練](./Training.md)成本低廉，但按[詞元](./Token.md)計費，是使用模型的主要費用來源。

_情境例句：_

「為什麼帳單會隨使用量計費，而不是固定授權費？」
"Why does the bill scale with usage instead of being a flat license?"

「你在為推論（Inference）付費——每次模型供應商請求都在供應商的硬體上執行模型。訓練早已完成，但推論費用按請求累計，而且一個[對話輪次](./Turn.md)在呼叫[工具](./Tool.md)時可能擴展成許多次請求。」
"You're paying for inference — every model provider request runs the model on the provider's hardware. Training already happened, but inference costs accrue per request, and a single [turn](./Turn.md) can expand into many requests when [tools](./Tool.md) are called."
