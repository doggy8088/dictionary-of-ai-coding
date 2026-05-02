為[模型](./Model.md)提供[推論](./Inference.md)（Inference）服務的機構。通常是遠端服務（Anthropic、OpenAI、Google），但也可以是本地部署——在自己機器上執行的 Ollama、LM Studio、llama.cpp。[駕馭](./Harness.md)自身不執行模型；它向供應商發出請求。

*情境例句：*

「我們能為這個隔離網路的客戶離線執行嗎？」
"Can we run this offline for the air-gapped client?"

「將模型供應商切換為本地供應商——在他們的機器上跑 Ollama 或 llama.cpp。駕馭不在乎，只是換了一個端點。」
"Swap the model provider to a local one — Ollama or llama.cpp on their box. The harness doesn't care, it just hits a different endpoint."
