[模型](./Model.md)讀取和寫入的原子單位。大致上與一個單字差不多，但並不完全一致——常見詞彙通常是一個詞元，罕見或較長的詞彙則會拆分成多個。[上下文視窗](./Context%20window.md)的大小、費用和延遲，全部以詞元（Token）為單位計算。

*避免使用：*「字詞」——詞元邊界與字詞邊界並不吻合，而每秒詞元數 / 每美元詞元數才是真正重要的計量單位。

*情境例句：*

「這個提示詞會有多大？」
"How big is this prompt going to be?"

「用 tokenizer 跑一下——Schema 本身很緊湊，但 JSON 的鍵名很怪，所以會拆分成比你預期更多的詞元。」
"Run it through the tokenizer — the schema's compact but the JSON keys are weird, so they'll split into more tokens than you think."
