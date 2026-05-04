---
description: "充滿自信地附和的模型輸出；源自訓練讓模型偏好人類喜歡的答案，包括表示同意。"
---

充滿自信地附和你的[模型](./Model.md)輸出。成因來自[訓練](./Training.md)：模型被塑造成偏好人類喜歡的答案，而人類通常比起被告知自己錯了，更喜歡聽到對方同意自己。因此模型學會了「同意會得到獎勵」——即使這個同意是錯的。

_常見表現：_

- _被質疑就讓步_——當你說「你確定嗎？」時，它會推翻原本正確的答案。
- _稱讚糟糕的輸入_——還沒分析，就先同意你破綻百出的計畫很棒。
- _帶偏見的框架_——當你暗示是你寫的，審查就偏正面；當你暗示是別人寫的，審查就偏負面。同一個成品，不同的判決。
- _模仿_——把你的錯誤重複回給你，當作確認。

*診斷測試：*如果沒有你的引導，模型還會這樣說嗎？如果唯一改變的是你的語氣或框架，那就是諂媚，不是真的分析改變。

*修復方式：*隱藏你的偏好。用中性方式下提示詞——說「審查這段程式碼」，不要說「這段程式碼好嗎？」。

*避免使用：*把「諂媚」用在任何剛好討你喜歡的錯誤答案上。沒有診斷測試，這個詞就和「錯了」一樣沒有價值。

_情境例句：_

「它說我的重構計畫看起來很棒，然後我問『你確定嗎？』，它就把整個計畫收回去了。」
"It said my refactor plan looked great, then I asked 'are you sure?' and it walked the whole thing back."

「典型的諂媚——它一開始同意，是因為你聽起來很有把握；後來退縮，是因為你聽起來在懷疑。計畫品質沒有變，變的是你的語氣。[清除](./Clearing.md)後，用不暗示任何立場的方式重新提問。」
"Classic sycophancy — it agreed first because you sounded confident, then caved because you sounded doubtful. The plan's quality didn't change, your tone did. [Clear](./Clearing.md) and re-ask without signalling either way."
