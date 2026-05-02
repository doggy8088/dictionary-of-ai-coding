[模型](./Model.md)內部的數字——通常有數十億個——在[訓練](./Training.md)過程中調整而成。模型「知道」的一切都存在於其中。訓練設定它們；[推論](./Inference.md)時保持不變地使用它們。又稱*權重*（weights）。

*情境例句：*

「我們可以在我們的程式碼庫上對它進行微調嗎？」
"Can we fine-tune it on our codebase?"

「那會更新參數——之後就是一個不同的模型了。對單一專案而言，把程式碼庫作為[脈絡](./Context.md)載入幾乎永遠比重新訓練便宜。」
"That'd update the parameters — different model afterwards. For one project it's almost always cheaper to load the codebase as [context](./Context.md) than to retrain."
