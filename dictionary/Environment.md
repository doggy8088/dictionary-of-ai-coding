---
description: "代理人行動的世界；駕馭外的一切，代理人透過工具結果感知，並透過工具呼叫改變。"
---

[代理人](./Agent.md)所作用的世界——[駕馭](./Harness.md)之外任何代理人透過[工具結果](./Tool%20result.md)感知、透過[工具呼叫](./Tool%20call.md)改變的一切。駕馭*執行*代理人；環境是代理人*工作的場所*。像 [`AGENTS.md`](./AGENTS.md.md) 這樣的檔案存在於環境中；駕馭負責將它載入[上下文視窗](./Context%20window.md)。[檔案系統](./Filesystem.md)（Filesystem）是最常見的環境類型，但並非唯一（資料庫、遠端 API、瀏覽器工作階段都可以是環境）。

_避免使用：_「環境」來指稱執行時期或駕馭本身——駕馭是外殼，環境是工作空間。

_情境例句：_

「代理人看不到 staging 資料庫的 Schema。」
"The agent can't see the staging DB schema."

「把它接入環境——給它一個只對 staging 具唯讀權限的 `psql` [工具](./Tool.md)。駕馭沒問題，只是它沒有任何東西可以作用。」
"Wire it into the environment — give it a `psql` [tool](./Tool.md) scoped to read-only on staging. The harness is fine, it just has nothing to act on."
