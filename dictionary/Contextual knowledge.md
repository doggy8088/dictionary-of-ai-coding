[代理人](./Agent.md)可以直接從當前[脈絡](./Context.md)中讀取的事實——使用者的任務指令、代理人已讀入的檔案、[工具結果](./Tool%20result.md)（Tool Results）、在[工作階段](./Session.md)開始時載入的 [AGENTS.md](./AGENTS.md.md) 內容。與[參數化知識](./Parametric%20knowledge.md)（Parametric Knowledge）相對：參數化知識是從參數中*召喚*出來的；情境知識是從[視窗](./Context%20window.md)中直接*讀取*的。當代理人從情境知識出發時，[幻覺](./Hallucination.md)（Hallucination）發生的機率大幅降低——答案就在眼前，無需從模糊的記憶中挖掘。

*只有在*與參數化知識對比時才使用此術語；其他情況直接說**脈絡**即可。

*避免使用：*「工作記憶體」——情境知識是當下在視窗裡的內容；[記憶系統](./Memory%20system.md)（Memory System）則是將跨工作階段的內容帶入其中的機制。兩者的尺度不同，不能混淆。

*情境例句：*

「為什麼我貼了 API 文件它就能對，不貼就亂說？」
"Why does it nail the API when I paste the docs and fabricate it when I don't?"

「貼了文件後，它讀的是情境知識——像在翻書查答案。沒貼的時候依賴的是參數化知識，那些少見的端點就會模糊。」
"With the docs in, it's contextual knowledge — reading off the page. Without, it's parametric and the rare endpoints blur."
