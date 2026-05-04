---
description: "以單元封裝的可教能力，包含某個任務的指令與資源，只有相關時才載入脈絡。"
---

一種可訓練的能力單元——針對某一項任務做好所需的指令和資源，存放在[環境](./Environment.md)中，只在相關時才載入[上下文視窗](./Context%20window.md)。這是[駕馭](./Harness.md)中實現[漸進式揭露](./Progressive%20disclosure.md)（Progressive Disclosure）的基本單位。

_避免使用：_「[工具](./Tool.md)」——工具是代理人*呼叫*的東西；技能（Skill）是代理人*讀取*的指令。

_情境例句：_

「部署操作手冊要放哪裡？」
"Where should I put the deploy runbook?"

「作為一個技能——代理人只在任務涉及部署時才載入它。放在 [AGENTS.md](./AGENTS.md.md) 裡，每個[對話輪次](./Turn.md)就要為一個每週只用一次的東西消耗[詞元](./Token.md)。」
"As a skill — the agent loads it only when the task involves deploys. In [AGENTS.md](./AGENTS.md.md) it'd burn [tokens](./Token.md) on every [turn](./Turn.md) for something we use weekly."
