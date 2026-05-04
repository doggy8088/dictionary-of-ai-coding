---
description: "會把資訊往後帶；工作階段跨對話輪次有狀態，代理人可透過記憶系統跨工作階段有狀態。"
---

攜帶資訊向前傳遞。一個[工作階段](./Session.md)在[對話輪次](./Turn.md)之間是有狀態的——[脈絡](./Context.md)在工作階段執行期間持續累積，這正是為何長工作階段會漂入[混沌區](./Smart%20zone.md)。代理人可以透過加入[記憶系統](./Memory%20system.md)（Memory System）跨**工作階段**保有狀態——將資訊持久化到[環境](./Environment.md)，並在未來工作階段開始時重新載入。[模型](./Model.md)永遠不是有狀態的；任何表面上的連續性都是[駕馭](./Harness.md)重新輸入脈絡的結果。與[無狀態](./Stateless.md)（Stateless）相對。

_情境例句：_

「它記得我昨天的偏好設定——這表示模型學到了嗎？」
"It remembered my preferences from yesterday — does that mean the model learned them?"

「沒有，代理人是有狀態的，因為駕馭把設定寫進了記憶檔案並在工作階段開始時重新載入。模型本身對昨天的事一無所知。」
"No, the agent's stateful because the harness wrote them to a memory file and reloaded them at session start. The model itself saw nothing of yesterday."
