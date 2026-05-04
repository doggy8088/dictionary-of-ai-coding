---
description: "在環境中執行的決定性驗證，例如測試、型別檢查、lint、建置與 pre-commit hook；只判斷通過或失敗。"
---

在[環境](./Environment.md)中執行的確定性驗證——測試、型別檢查、靜態分析（lint）、建置、pre-commit hooks。結果只有通過或失敗，不涉及判斷。這是[代理人](./Agent.md)可以自行修正、無需任何人介入的訊號。不穩定的測試是壞掉的自動化檢查，而非不算數的檢查；自動化檢查就是要設計成確定性的。

_避免使用：_「回饋迴路」、「反壓」——這兩個詞把自動化檢查和[審查](./Automated%20review.md)混為一談。_避免使用：_「測試」——測試是自動化檢查的一種，但並非所有自動化檢查都是測試。

_情境例句：_

「代理人在 [AFK](./AFK.md) 執行時一直交出有問題的程式碼。」
"The agent keeps shipping broken code in the [AFK](./AFK.md) runs."

「[沙盒](./Sandbox.md)裡接了哪些自動化檢查？」
"What automated checks are wired into the [sandbox](./Sandbox.md)?"

「只有單元測試。」
"Just the unit tests."

「加上型別檢查和靜態分析——它在 PR 送出之前就能自行從這些結果修正。」
"Add typecheck and lint — it'll self-correct from those before the PR ever lands."
