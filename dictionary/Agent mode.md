---
aliases:
  - plan mode
  - accept-edits
  - bypass permissions
  - YOLO mode
---
一種在執行時期形塑[代理人](./Agent.md)（Agent）運作方式的預設組合——將[權限模式](./Permission%20mode.md)（Permission Mode）與注入[系統提示詞](./System%20prompt.md)（System Prompt）的行為指令捆綁在一起。常見範例：預設模式（針對風險操作請求確認）、**計劃模式**（plan mode，封鎖編輯並引導代理人進行研究）、**自動接受編輯**模式（accept-edits，自動核准編輯）、**繞過權限**模式（bypass permissions，俗稱 **YOLO 模式**，自動核准一切）。可在[工作階段](./Session.md)進行中切換。

*廠商術語：* Claude Code 將這些稱為「permission modes」（權限模式），Codex 稱為「approval modes」（核准模式）——兩者均早於行為捆綁概念的出現。

*情境例句：*

「它一直修改檔案，但我只想要一份計劃。」
"It keeps editing files when I just want a plan."

「切換到計劃模式——它會封鎖寫入，並保持在研究階段。」
"Switch to plan mode — it'll block writes and stay in research."

「那之後的 [AFK](./AFK.md) 執行呢？」
"What about for the [AFK](./AFK.md) run later?"

「繞過模式，但只在[沙盒](./Sandbox.md)（Sandbox）裡用。」
"Bypass mode, but only inside the [sandbox](./Sandbox.md)."
