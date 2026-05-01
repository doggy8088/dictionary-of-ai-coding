設定[模型](./Model.md)[參數](./Parameters.md)（Parameters）的過程——將模型暴露於大量文字，並調整參數以改善[下一個詞元預測](./Next-token%20prediction.md)的準確性。由[模型供應商](./Model%20provider.md)（Model Provider）執行的一次性、高成本過程。涵蓋預訓練（pre-training，主要的大規模執行）和後訓練（post-training，後續的精煉，如指令遵循和安全性校準）；在本詞彙表的層次，這個區別並不重要。

*使用範例：*

「我們能讓它學習我們的內部 API 嗎？」

「不能透過訓練——那是模型供應商執行的、耗時數月的過程。改為把 API 文件載入[脈絡](./Context.md)，那才是你實際能用的槓桿。」
