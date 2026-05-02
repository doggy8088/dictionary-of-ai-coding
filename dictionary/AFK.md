---
aliases:
  - away from keyboard
  - AFK (away from keyboard)
---
一種工作模式，使用者啟動一個[工作階段](./Session.md)後便離開，讓[代理人](./Agent.md)（Agent）無人監督地獨立執行。這是 AI Coding 的吞吐量倍增器——在你睡覺、吃飯或處理其他事情時，可以同時並行執行多個 AFK 工作階段。通常需要寬鬆的[權限模式](./Permission%20mode.md)（Permission Mode）搭配[沙盒](./Sandbox.md)（Sandbox）機制才能安全運作。

*避免使用：*「背景代理人」——這個說法以機器為中心（「在背景執行」），而非以人的行為模式為中心（「使用者已離開」）。AFK 的核心事實是：使用者不在監看。

*情境例句：*

「我要讓這個工作 AFK 執行——三個沙盒化的代理人負責重構，早上再來審查 PR。」
"I'm running this AFK — three sandboxed agents on the refactor, reviewing the PRs in the morning."

「要[繞過權限](./Agent%20mode.md)嗎？」
"[Bypass permissions](./Agent%20mode.md)?"

「對，唯讀[檔案系統](./Filesystem.md)，不連外網。」
"Yeah, read-only [filesystem](./Filesystem.md), no network."
