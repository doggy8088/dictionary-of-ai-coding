---
description: "把代理人脈絡從一個工作階段轉移到另一個工作階段，且沒有返回路徑；承載機制可變。"
---

將[代理人](./Agent.md)的[脈絡](./Context.md)從一個[工作階段](./Session.md)轉移到另一個，且沒有返回路徑。傳遞方式各異——可以是書面的[交接文件](./Handoff%20artifact.md)（Handoff Artifact）、記憶體內的摘要（[壓縮摘要](./Compaction.md)），或其他方式。與[清除](./Clearing.md)（Clearing）不同——清除不進行任何轉移。進行交接的原因多樣：切換角色（規劃者→實作者）、啟動 [AFK](./AFK.md) 執行、分散到並行工作階段，或釋放[上下文視窗](./Context%20window.md)空間。

_情境例句：_

「規劃工作階段越來越沉重——我應該繼續撐下去嗎？」
"Planning session is getting heavy — should I just keep going?"

「做一次交接。把決策寫進文件，清除工作階段，然後在新的工作階段中讀取那份文件來開始實作。」
"Do a handoff. Write the decisions to a doc, clear, start the implementation in a fresh session reading from it."
