---
description: "把外部工具伺服器接入駕馭的協定，讓代理人取得駕馭本身沒有內建的工具。"
---

**模型脈絡協定（Model Context Protocol）。** 一種把外部工具伺服器接入[駕馭](./Harness.md)的協定——讓[代理人](./Agent.md)取得駕馭本身沒有內建的[工具](./Tool.md)。代理人從來不會「呼叫 MCP」；它呼叫的是工具，只是駕馭剛好是從 MCP 伺服器取得那個工具。MCP 也會暴露資源（唯讀資料）與提示詞（可重用範本），但提供工具是主要用途。

_情境例句：_

「代理人需要從 Linear 讀取 ticket。」
"The agent needs to read tickets from Linear."

「設定駕馭使用 Linear MCP 伺服器——它會把 Linear API 暴露成代理人可呼叫的工具。這樣就不用自己寫工具包裝器。」
"Configure the harness to use the Linear MCP server — it exposes the Linear API as tools the agent can call. Saves you writing custom tool wrappers."
