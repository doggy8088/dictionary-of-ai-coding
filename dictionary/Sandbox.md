---
description: "代理人執行所在的隔離環境，例如容器、VM 或受限 shell；用來限制代理人動作的爆炸半徑。"
aliases:
  - Sandboxing
  - Sandbox / Sandboxing
---

[代理人](./Agent.md)在其中執行的隔離[環境](./Environment.md)——一個容器、虛擬機、臨時[檔案系統](./Filesystem.md)或受限權限的 shell。限制代理人操作的影響範圍：即使代理人執行了破壞性指令或下載了惡意內容，損害也被控制在沙盒之內。這是讓 [AFK](./AFK.md) 工作模式在實務上可行的安全基礎。

_情境例句：_

「我想讓它在繞過權限模式下跑一夜，但又擔心風險。」
"I want to let it run [bypass-permissions](./Agent%20mode.md) overnight but I'm not ready for that."

「把它放進沙盒（Sandbox）——全新容器、不掛載任何憑證、不開外網。最壞的情況是它毀掉自己的檔案系統，然後你丟棄那個容器就好了。」
"Put it in a sandbox — fresh container, no credentials mounted, no network out. Worst case it nukes its own filesystem and you discard the container."
