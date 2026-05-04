---
description: "駕馭暴露給代理人呼叫的函式，例如讀取、寫入、Bash、搜尋；代理人靠它感知並作用於環境。"
---

[駕馭](./Harness.md)暴露給[代理人](./Agent.md)可以呼叫的函式——Read（讀取）、Write（寫入）、Bash（執行指令）、Search（搜尋）。工具是代理人感知並作用於[環境](./Environment.md)的方式：代理人除了透過[工具結果](./Tool%20result.md)之外無法感知環境，除了透過[工具呼叫](./Tool%20call.md)之外無法改變環境。每次工具呼叫都需要額外一次[模型供應商請求](./Model%20provider%20request.md)，因為結果必須返回給模型，模型才能決定下一步。

_情境例句：_

「代理人可以直接查詢 staging 資料庫嗎？」
"Can the agent query staging directly?"

「在駕馭裡加一個 `psql` 工具，限定只對 staging 具唯讀權限。沒有對應工具的話，代理人對[檔案系統](./Filesystem.md)之外的一切都是盲的。」
"Add a `psql` tool to the harness, scoped read-only on staging. Without a tool for it, the agent's blind to anything outside the [filesystem](./Filesystem.md)."
