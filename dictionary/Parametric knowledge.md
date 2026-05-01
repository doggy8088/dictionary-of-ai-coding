[模型](./Model.md)從[訓練](./Training.md)中「學到」的知識，儲存在其[參數](./Parameters.md)中。在訓練時凍結——模型既看不到自己的參數，也無法更新它們。資訊在壓縮時會流失：數十億個事實被塞進固定數量的參數，稀少的細節因此變得模糊。是流暢處理常見主題的來源，也是在不常見主題上產生捏造的根源。與[情境知識](./Contextual%20knowledge.md)（Contextual Knowledge）相對。

*使用範例：*

「它寫的 React 無懈可擊，但對我們內部 SDK 的方法卻亂說一通。」

「React 在參數化知識（Parametric Knowledge）裡密度很高——有數百萬個訓練範例。你們的 SDK 沒有，所以模型填入看起來合理的形狀。把 SDK 文件載入[脈絡](./Context.md)裡。」
