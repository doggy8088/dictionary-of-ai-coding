<!--
  GENERATED FILE — DO NOT EDIT.
  Source: dictionary/*.md, internal/Curriculum.md, internal/README.template.md
  Regenerate: npm run generate
-->

# AI Coding 詞彙字典

**AI Coding 常常讓人感覺是專家的專利**。一堆沒有解釋的術語。莫名其妙的失敗。帳單金額與實際工作量對不上。

其實沒那麼難。很多困惑都是人為製造的：**有一整個靠風投支撐的生態圈，從讓這些東西難以理解中獲益**。

AI Coding 的基本術語，一個下午就能學完。掌握了這些術語，整件事就不再像是猜謎遊戲。

為什麼脈絡（Context）會衰退？為什麼帳單這麼高？為什麼同一個提示詞，今天和昨天的行為不一樣？

每個問題都有清晰的答案，只要有人告訴你該用什麼詞。

這就是這本字典的用途。**AI Coding 的詞彙，用清晰的語言翻譯給你**。

**想要的不只是詞彙？** 加入 62,000+ 位開發者，訂閱 **[aihero.dev/newsletter](https://www.aihero.dev/s/dictionary-newsletter)**，獲取我最新的技能、AI 工程思考，以及讓你保持領先的資源。

---

## 目錄

<details markdown="1">
<summary>Section 1 — 模型</summary>

- [Model](#model)
- [Parameters](#parameters)
- [Training](#training)
- [Inference](#inference)
- [Token](#token)
- [Next-token prediction](#next-token-prediction)
- [Model provider](#model-provider)
- [Harness](#harness)
- [Model provider request](#model-provider-request)
- [Input tokens](#input-tokens)
- [Output tokens](#output-tokens)
- [Prefix cache](#prefix-cache)
- [Cache tokens](#cache-tokens)

</details>

<details markdown="1">
<summary>Section 2 — 工作階段、上下文視窗與對話輪次</summary>

- [Stateless](#stateless)
- [Context](#context)
- [Context window](#context-window)
- [Stateful](#stateful)
- [Agent](#agent)
- [System prompt](#system-prompt)
- [Session](#session)
- [Turn](#turn)

</details>

<details markdown="1">
<summary>Section 3 — 工具與環境</summary>

- [Environment](#environment)
- [Filesystem](#filesystem)
- [Tool](#tool)
- [Tool call](#tool-call)
- [Tool result](#tool-result)
- [Permission request](#permission-request)
- [Permission mode](#permission-mode)
- [Agent mode](#agent-mode)
- [Sandbox](#sandbox)

</details>

<details markdown="1">
<summary>Section 4 — 幻覺及其成因</summary>

- [Hallucination](#hallucination)
- [Parametric knowledge](#parametric-knowledge)
- [Knowledge cutoff](#knowledge-cutoff)
- [Contextual knowledge](#contextual-knowledge)
- [Attention relationship](#attention-relationship)
- [Attention budget](#attention-budget)
- [Attention degradation](#attention-degradation)
- [Smart zone](#smart-zone)

</details>

<details markdown="1">
<summary>Section 5 — 交接</summary>

- [Clearing](#clearing)
- [Handoff](#handoff)
- [Handoff artifact](#handoff-artifact)
- [Spec](#spec)
- [Ticket](#ticket)
- [Compaction](#compaction)
- [Autocompact](#autocompact)

</details>

<details markdown="1">
<summary>Section 6 — 記憶與引導</summary>

- [Memory system](#memory-system)
- [AGENTS.md](#agentsmd)
- [Progressive disclosure](#progressive-disclosure)
- [Skill](#skill)
- [Subagent](#subagent)

</details>

<details markdown="1">
<summary>Section 7 — 工作模式</summary>

- [Human-in-the-loop](#human-in-the-loop)
- [AFK](#afk)
- [Automated check](#automated-check)
- [Automated review](#automated-review)
- [Human review](#human-review)
- [Vibe coding](#vibe-coding)
- [Design concept](#design-concept)
- [Grilling](#grilling)

</details>

## Section 1 — 模型

### Model

即[參數](#parameters)（Parameters）本身。[無狀態](#stateless)（Stateless）——執行[下一個詞元預測](#next-token-prediction)，僅此而已。「Claude Opus 4.7」和「GPT-5」都是模型。模型本身無法做任何代理人該做的事；它必須被[駕馭化](#harness)（Harnessed）。

*使用範例：*

「規劃步驟要不要把模型從 Sonnet 換成 Opus？」

「試試看吧——但這個任務大部分工作是駕馭在做。如果[系統提示詞](#system-prompt)和[工具](#tool)設定不對，換模型也沒用。」

### Parameters

[模型](#model)內部的數字——通常有數十億個——在[訓練](#training)過程中調整而成。模型「知道」的一切都存在於其中。訓練設定它們；[推論](#inference)時保持不變地使用它們。又稱*權重*（weights）。

*使用範例：*

「我們可以在我們的程式碼庫上對它進行微調嗎？」

「那會更新參數——之後就是一個不同的模型了。對單一專案而言，把程式碼庫作為[脈絡](#context)載入幾乎永遠比重新訓練便宜。」

### Training

設定[模型](#model)[參數](#parameters)（Parameters）的過程——將模型暴露於大量文字，並調整參數以改善[下一個詞元預測](#next-token-prediction)的準確性。由[模型供應商](#model-provider)（Model Provider）執行的一次性、高成本過程。涵蓋預訓練（pre-training，主要的大規模執行）和後訓練（post-training，後續的精煉，如指令遵循和安全性校準）；在本詞彙表的層次，這個區別並不重要。

*使用範例：*

「我們能讓它學習我們的內部 API 嗎？」

「不能透過訓練——那是模型供應商執行的、耗時數月的過程。改為把 API 文件載入[脈絡](#context)，那才是你實際能用的槓桿。」

### Inference

執行已訓練好的[模型](#model)以產生輸出——每次[模型供應商請求](#model-provider-request)（Model Provider Request）都在做這件事。[參數](#parameters)（Parameters）維持不變；模型只是對給定的[脈絡](#context)進行[下一個詞元預測](#next-token-prediction)。相較於[訓練](#training)成本低廉，但按[詞元](#token)計費，是使用模型的主要費用來源。

*使用範例：*

「為什麼帳單會隨使用量計費，而不是固定授權費？」

「你在為推論（Inference）付費——每次模型供應商請求都在供應商的硬體上執行模型。訓練早已完成，但推論費用按請求累計，而且一個[對話輪次](#turn)在呼叫[工具](#tool)時可能擴展成許多次請求。」

### Token

[模型](#model)讀取和寫入的原子單位。大致上與一個單字差不多，但並不完全一致——常見詞彙通常是一個詞元，罕見或較長的詞彙則會拆分成多個。[上下文視窗](#context-window)的大小、費用和延遲，全部以詞元（Token）為單位計算。

*避免使用：*「字詞」——詞元邊界與字詞邊界並不吻合，而每秒詞元數 / 每美元詞元數才是真正重要的計量單位。

*使用範例：*

「這個提示詞會有多大？」

「用 tokenizer 跑一下——Schema 本身很緊湊，但 JSON 的鍵名很怪，所以會拆分成比你預期更多的詞元。」

### Next-token prediction

[模型](#model)實際上做的事。給定一個[脈絡](#context)，它抽樣出下一個[詞元](#token)，將其附加上去，然後再執行一遍。所有輸出——一個句子、一個[工具呼叫](#tool-call)、一個上千行的檔案——都是逐個詞元建構起來的。模型沒有其他運作模式。

*使用範例：*

「[代理人](#agent)是怎麼『決定』要呼叫一個工具的？」

「它不是『決定』——一路到底都是下一個詞元預測（Next-Token Prediction）。工具呼叫不過是[駕馭](#harness)從輸出串流中解析出來的一個結構化字串。」

### Model provider

為[模型](#model)提供[推論](#inference)（Inference）服務的機構。通常是遠端服務（Anthropic、OpenAI、Google），但也可以是本地部署——在自己機器上執行的 Ollama、LM Studio、llama.cpp。[駕馭](#harness)自身不執行模型；它向供應商發出請求。

*使用範例：*

「我們能為這個隔離網路的客戶離線執行嗎？」

「將模型供應商切換為本地供應商——在他們的機器上跑 Ollama 或 llama.cpp。駕馭不在乎，只是換了一個端點。」

### Harness

圍繞[模型](#model)、將其轉化為[代理人](#agent)的一切：[工具](#tool)、[系統提示詞](#system-prompt)、[上下文視窗](#context-window)管理、權限設定、hooks。**Claude.ai** 和 **Claude Code** 執行的是同一個模型，行為卻大相徑庭，原因正是它們的駕馭不同。

*使用範例：*

「同樣的模型，為什麼 Claude Code 會修改檔案，而 Claude.ai 只是回答問題？」

「駕馭不同——Claude Code 有[檔案系統](#filesystem)工具、不同的系統提示詞和權限層。模型不是變數所在。」

### Model provider request

從[駕馭](#harness)到[模型供應商](#model-provider)的一次往返。駕馭發送當前[脈絡](#context)；供應商回傳一個回應（一個[工具呼叫](#tool-call)或最終答案）。如果[代理人](#agent)呼叫[工具](#tool)，一條使用者訊息可能觸發許多次模型供應商請求——每個[工具結果](#tool-result)都會觸發另一次請求。

*使用範例：*

「一個問題燒了四萬個[詞元](#token)？」

「看看工具呼叫——十二次 grep、八次讀取、四次編輯。每個工具結果都會觸發另一次模型供應商請求，而整個[工作階段](#session)的前綴每次都要重新發送。」

### Input tokens

[駕馭](#harness)（Harness）在每次[模型供應商請求](#model-provider-request)時發送的[詞元](#token)。計費費率低於[輸出詞元](#output-tokens)（Output Tokens）。

*使用範例：*

「帳單很高，但[代理人](#agent)寫出的內容很少。」

「是輸入詞元（Input Tokens）的問題——每個[對話輪次](#turn)都重新發送整個[工作階段](#session)的歷史。沒有[前綴快取](#prefix-cache)（Prefix Cache）的話，每次請求都要重新為歷史記錄付費。」

### Output tokens

[模型](#model)產生回傳的[詞元](#token)。計費費率高於[輸入詞元](#input-tokens)，因為產生輸出需要更多運算。

*使用範例：*

「這次重構[工作階段](#session)燒信用額度燒得很兇，明明輸入很小。」

「[代理人](#agent)在整檔重寫，而不是局部修補。輸出詞元（Output Tokens）的費率大約是輸入費率的五倍——讓它只輸出差異（edits），帳單就會降下來。」

### Prefix cache

[供應商](#model-provider)端的快取儲存區，讓連續的[模型供應商請求](#model-provider-request)能夠跳過重新處理共享前綴的步驟。當一個請求的開頭與近期某個請求的開頭吻合——相同的[系統提示詞](#system-prompt)、相同的歷史記錄到某個時間點——供應商就重複使用先前的運算結果，並以[快取詞元](#cache-tokens)（Cache Tokens）的折扣費率計費。

任何改變前綴的操作（重新排列檔案順序、在[工作階段](#session)中途改寫系統提示詞、在頂部注入時間戳記）都會從該點起使快取失效，之後的請求以全額[輸入詞元](#input-tokens)費率計費。

*使用範例：*

「為什麼帳單在工作階段中途突然飆高？」

「[駕馭](#harness)開始在每個[對話輪次](#turn)把當前時間注入系統提示詞。前綴快取在第一個改變的詞元處就失效了，所以此後每次請求都以全額費率計費。」

### Cache tokens

[供應商](#model-provider)（Model Provider）從先前的[模型供應商請求](#model-provider-request)（Model Provider Request）快取下來的[輸入詞元](#input-tokens)（Input Tokens），不必重新處理。當連續的請求共享同一個前綴時，供應商透過其[前綴快取](#prefix-cache)（Prefix Cache）重複使用先前的運算結果，並以大幅折扣的費率計費快取部分。這是讓長[工作階段](#session)在成本上可行的關鍵機制——沒有它，每個[對話輪次](#turn)都要重新支付整段歷史的費用。

*使用範例：*

「長工作階段的費用很驚人——一次重構花了八美元。」

「看看快取詞元（Cache Tokens）。如果[駕馭](#harness)在輪次之間重新排列[系統提示詞](#system-prompt)或檔案，前綴就會失效，每次請求都要以全額輸入詞元費率重新計費。」

## Section 2 — 工作階段、上下文視窗與對話輪次

### Stateless

不攜帶任何資訊向前傳遞。[模型](#model)在[模型供應商請求](#model-provider-request)（Model Provider Requests）之間是無狀態的——每次請求重新發送完整的[上下文視窗](#context-window)，因為模型無法看到其他任何東西。[代理人](#agent)預設在[工作階段](#session)之間是無狀態的：新工作階段從空白開始，沒有任何先前工作階段的痕跡。與[有狀態](#stateful)（Stateful）相對。

*使用範例：*

「為什麼每次我[清除](#clearing)之後它就忘記了那個慣例？」

「模型是無狀態的——新工作階段從空白開始。如果你想保留它，就把它寫入 [AGENTS.md](#agentsmd) 或一個[駕馭](#harness)在工作階段開始時會載入的記憶檔案。」

### Context

[代理人](#agent)目前可以存取的相關資訊。這是一個抽象名詞——不是模型看到的原始輸入（那是[上下文視窗](#context-window)），也不是持續累積的對話歷史（那是[工作階段](#session)），而是*代理人當下對任務而言切實可用的知識*。「將某樣東西載入脈絡」意味著把它納入這個集合；「脈絡工程」（Context Engineering）是策劃和管理這個集合的學問。

*使用範例：*

「它不斷捏造型別裡根本不存在的欄位。」

「型別檔沒有進脈絡——它在讀呼叫端然後猜。先把定義讀進來。」

### Context window

模型在每次[模型供應商請求](#model-provider-request)（Model Provider Request）中所能看到的全部內容。容量有限、因模型而異，且是*模型感知任何事物的唯一介面*。

*避免使用：*「記憶體」——上下文視窗是工作狀態，不會跨[工作階段](#session)持久保存。[記憶體](#memory-system)（Memory）是一個獨立概念，架構在其上層。

*使用範例：*

「我可以把整個 monorepo 貼到提示詞裡嗎？」

「上下文視窗有 20 萬個[詞元](#token)——大概只是整個代碼庫的五分之一。選取任務會觸及的檔案，把其餘的留在[工具呼叫](#tool-call)後面按需載入。」

### Stateful

攜帶資訊向前傳遞。一個[工作階段](#session)在[對話輪次](#turn)之間是有狀態的——[脈絡](#context)在工作階段執行期間持續累積，這正是為何長工作階段會漂入[混沌區](#smart-zone)。代理人可以透過加入[記憶系統](#memory-system)（Memory System）跨**工作階段**保有狀態——將資訊持久化到[環境](#environment)，並在未來工作階段開始時重新載入。[模型](#model)永遠不是有狀態的；任何表面上的連續性都是[駕馭](#harness)重新輸入脈絡的結果。與[無狀態](#stateless)（Stateless）相對。

*使用範例：*

「它記得我昨天的偏好設定——這表示模型學到了嗎？」

「沒有，代理人是有狀態的，因為駕馭把設定寫進了記憶檔案並在工作階段開始時重新載入。模型本身對昨天的事一無所知。」

### Agent

一個配備了[工具](#tool)（Tools）、[系統提示詞](#system-prompt)（System Prompt）和[上下文視窗](#context-window)（Context Window）的[模型](#model)（Model），透過[對話輪次](#turn)與使用者互動。*Claude Code 是代理人。Cursor 是代理人。Claude.ai 是代理人。* 代理人是你實際與之對話的存在——是運作中的模型，針對特定目的進行配置。

*避免使用：*「AI」、「機器人」（too vague — 這些說法過於模糊，無法區分你指的是模型參數本身，還是經過駕馭化的整體系統）。

*使用範例：*

「你用哪個代理人來跑這次的遷移作業？」

「本地用 Claude Code，UI 部分用 Cursor——底層是同一個模型，駕馭不同。」

### System prompt

[駕馭](#harness)在每次[模型供應商請求](#model-provider-request)前都會加入的指令——[代理人](#agent)的常駐任務說明書：它是誰、如何行事、可以呼叫哪些[工具](#tool)、應遵循哪些慣例。通常在整個[工作階段](#session)期間保持穩定。

*使用範例：*

「兩個駕馭、同一個[模型](#model)，同樣的提示詞行為卻截然不同。」

「系統提示詞不同。一個調整為精簡的程式碼編輯，另一個調整為解釋說明——差異就在那裡，在你的訊息到達之前就已決定了。」

### Session

與[代理人](#agent)進行的單次有界互動。從空白開始，逐漸累積訊息、[工具結果](#tool-result)和讀取的檔案，並在[清除](#clearing)、關閉或[壓縮摘要](#compaction)成新工作階段時結束。工作階段是*填充*[上下文視窗](#context-window)的東西：如果上下文視窗是個盒子，工作階段就是慢慢將它填滿的內容。超出單個上下文視窗容量的工作，必須拆分到多個工作階段中進行。

*使用範例：*

「一個工作階段能跑多久才不至於崩潰？」

「取決於工作的性質——一次專注的重構保持清晰的時間比開放式研究長得多。一旦工作階段過於龐大，就[交接](#handoff)或壓縮摘要，不要硬撐。」

### Turn

一條使用者訊息，加上[代理人](#agent)在回應中所做的一切，直到它將控制權還給使用者為止。包含一次或多次[模型供應商請求](#model-provider-request)——如果代理人呼叫[工具](#tool)，則可能包含許多次。一個澄清問題結束這個輪次；你的回覆開始下一個。層級關係是[工作階段](#session) **> 對話輪次（Turn）> 模型供應商請求**。

*使用範例：*

「一個輪次花了兩分鐘？」

「它在那個輪次裡發出了十四次[工具呼叫](#tool-call)——每次都是一個獨立的模型供應商請求。延遲不斷疊加，直到代理人最終把控制權還給你。」

## Section 3 — 工具與環境

### Environment

[代理人](#agent)所作用的世界——[駕馭](#harness)之外任何代理人透過[工具結果](#tool-result)感知、透過[工具呼叫](#tool-call)改變的一切。駕馭*執行*代理人；環境是代理人*工作的場所*。像 [`AGENTS.md`](#agentsmd) 這樣的檔案存在於環境中；駕馭負責將它載入[上下文視窗](#context-window)。[檔案系統](#filesystem)（Filesystem）是最常見的環境類型，但並非唯一（資料庫、遠端 API、瀏覽器工作階段都可以是環境）。

*避免使用：*「環境」來指稱執行時期或駕馭本身——駕馭是外殼，環境是工作空間。

*使用範例：*

「代理人看不到 staging 資料庫的 Schema。」

「把它接入環境——給它一個只對 staging 具唯讀權限的 `psql` [工具](#tool)。駕馭沒問題，只是它沒有任何東西可以作用。」

### Filesystem

[代理人](#agent)讀取、寫入、並在其中執行程式的檔案與目錄樹——coding agent 預設的[環境](#environment)類型。[AGENTS.md](#agentsmd)、[技能](#skill)（Skills）、原始碼、建置腳本和[工具](#tool)配置，全都存放在檔案系統中。當一個[駕馭](#harness)「從你的專案啟動」時，它就是在將代理人指向一個檔案系統。

*使用範例：*

「它為什麼沒有讀到我的 AGENTS.md？」

「它跑的是另一個檔案系統——[沙盒](#sandbox)掛載了上層目錄，而不是專案根目錄。重新指定駕馭的路徑。」

### Tool

[駕馭](#harness)暴露給[代理人](#agent)可以呼叫的函式——Read（讀取）、Write（寫入）、Bash（執行指令）、Search（搜尋）。工具是代理人感知並作用於[環境](#environment)的方式：代理人除了透過[工具結果](#tool-result)之外無法感知環境，除了透過[工具呼叫](#tool-call)之外無法改變環境。每次工具呼叫都需要額外一次[模型供應商請求](#model-provider-request)，因為結果必須返回給模型，模型才能決定下一步。

*使用範例：*

「代理人可以直接查詢 staging 資料庫嗎？」

「在駕馭裡加一個 `psql` 工具，限定只對 staging 具唯讀權限。沒有對應工具的話，代理人對[檔案系統](#filesystem)之外的一切都是盲的。」

### Tool call

[模型](#model)輸出的、指定某個[工具](#tool)及其參數的內容——這不過是結構化文字。它本身不做任何事；[駕馭](#harness)必須讀取它並執行。由模型在一次[模型供應商請求](#model-provider-request)中產生。

*使用範例：*

「它說它跑了測試，但檔案的時間戳記沒有變。」

「看一下對話紀錄——它是真的發出了工具呼叫，還是只是描述跑了測試？模型產生呼叫指令，但如果駕馭沒有執行它，什麼都沒發生。」

### Tool result

[駕馭](#harness)執行[工具呼叫](#tool-call)後回傳的內容——檔案內容、指令輸出、錯誤訊息。這是[代理人](#agent)感知[環境](#environment)的唯一窗口。在*下一次*[模型供應商請求](#model-provider-request)中傳回[模型](#model)，模型才能決定如何處理它。工具呼叫和工具結果是同一次交換的兩端，都發生在同一個[對話輪次](#turn)之內。

*使用範例：*

「它在推論這個檔案的內容時，好像把它當成空的。」

「工具結果回傳的是權限拒絕，不是檔案內容。模型只看到了錯誤字串——它沒有任何其他窗口可以看見這個檔案。」

### Permission request

[駕馭](#harness)在執行未預先核准的[工具呼叫](#tool-call)前，向使用者展示的提示。[模型](#model)產生工具呼叫；駕馭不立即執行，而是暫停並詢問使用者。核准則執行；拒絕則駕馭將拒絕結果作為[工具結果](#tool-result)回報給模型。這是駕馭讓人類加入[迴圈](#human-in-the-loop)以監督風險或敏感操作的機制。

*使用範例：*

「它被一個權限請求卡住十分鐘了——我開會去了。」

「這就是人在迴圈的代價。預先核准安全的[工具](#tool)，讓請求只在真正有風險的操作上觸發。」

### Permission mode

[代理人模式](#agent-mode)（Agent Mode）中負責權限把關的切片——哪些[工具呼叫](#tool-call)會觸發[權限請求](#permission-request)（Permission Request），哪些會自動執行。這是模式系統的原始用途，後來[駕馭](#harness)才開始在其上捆綁行為指令。

*使用範例：*

「它每次 grep 都暫停——[AFK](#afk) 執行完全被卡死了。」

「放寬唯讀[工具](#tool)的權限模式，保留對寫入和 shell 操作的提示。研究型[工作階段](#session)裡大多數的權限請求都是雜訊。」

### Agent mode

一種在執行時期形塑[代理人](#agent)（Agent）運作方式的預設組合——將[權限模式](#permission-mode)（Permission Mode）與注入[系統提示詞](#system-prompt)（System Prompt）的行為指令捆綁在一起。常見範例：預設模式（針對風險操作請求確認）、**計劃模式**（plan mode，封鎖編輯並引導代理人進行研究）、**自動接受編輯**模式（accept-edits，自動核准編輯）、**繞過權限**模式（bypass permissions，俗稱 **YOLO 模式**，自動核准一切）。可在[工作階段](#session)進行中切換。

*廠商術語：* Claude Code 將這些稱為「permission modes」（權限模式），Codex 稱為「approval modes」（核准模式）——兩者均早於行為捆綁概念的出現。

*使用範例：*

「它一直修改檔案，但我只想要一份計劃。」

「切換到計劃模式——它會封鎖寫入，並保持在研究階段。」

「那之後的 [AFK](#afk) 執行呢？」

「繞過模式，但只在[沙盒](#sandbox)（Sandbox）裡用。」

### Sandbox

[代理人](#agent)在其中執行的隔離[環境](#environment)——一個容器、虛擬機、臨時[檔案系統](#filesystem)或受限權限的 shell。限制代理人操作的影響範圍：即使代理人執行了破壞性指令或下載了惡意內容，損害也被控制在沙盒之內。這是讓 [AFK](#afk) 工作模式在實務上可行的安全基礎。

*使用範例：*

「我想讓它在繞過權限模式下跑一夜，但又擔心風險。」

「把它放進沙盒（Sandbox）——全新容器、不掛載任何憑證、不開外網。最壞的情況是它毀掉自己的檔案系統，然後你丟棄那個容器就好了。」

## Section 4 — 幻覺及其成因

### Hallucination

充滿自信卻又錯誤的[模型](#model)輸出。分為兩種類型，各有不同的成因與修復方式：

- *事實性幻覺*（Factuality Hallucination）——捏造或錯誤的世界知識（一個不存在的函式、錯誤的 API 簽名、虛假的引用來源）。成因是[參數化知識](#parametric-knowledge)的缺口，常發生在[知識截止日期](#knowledge-cutoff)之後的內容。修復方式：載入正確的[情境知識](#contextual-knowledge)。
- *忠實性幻覺*（Faithfulness Hallucination）——輸出偏離了已載入的**情境知識**、使用者的指令，或模型自身先前的推理。這是[注意力衰退](#attention-degradation)（Attention Degradation）的症狀，在[混沌區](#smart-zone)會更嚴重。修復方式：[清除](#clearing)或[壓縮摘要](#compaction)。

*避免使用：*「幻覺」作為「錯誤」的代名詞——不指明是哪種類型，這個詞就沒有任何診斷價值。

*使用範例：*

「它幻覺出了 Schema 上一個 `parseAsync` 方法。」

「是事實性還是忠實性幻覺？」

「那個方法在我貼的文件裡有——它只是在第四十個[對話輪次](#turn)後停止讀那份文件了。」

「那就是忠實性幻覺。壓縮摘要並重新載入，不用再加更多文件了。」

### Parametric knowledge

[模型](#model)從[訓練](#training)中「學到」的知識，儲存在其[參數](#parameters)中。在訓練時凍結——模型既看不到自己的參數，也無法更新它們。資訊在壓縮時會流失：數十億個事實被塞進固定數量的參數，稀少的細節因此變得模糊。是流暢處理常見主題的來源，也是在不常見主題上產生捏造的根源。與[情境知識](#contextual-knowledge)（Contextual Knowledge）相對。

*使用範例：*

「它寫的 React 無懈可擊，但對我們內部 SDK 的方法卻亂說一通。」

「React 在參數化知識（Parametric Knowledge）裡密度很高——有數百萬個訓練範例。你們的 SDK 沒有，所以模型填入看起來合理的形狀。把 SDK 文件載入[脈絡](#context)裡。」

### Knowledge cutoff

[模型](#model)不具備[參數化知識](#parametric-knowledge)（Parametric Knowledge）的日期。截止日期之後的函式庫、API 和事件，除非以[情境知識](#contextual-knowledge)的形式載入文件，否則都是捏造的溫床。每次模型發布都有各自的截止日期。

*使用範例：*

「它一直寫 v3 SDK 的語法——我們用的是 v5。」

「v5 是在知識截止日期之後才發布的。把 v5 的 changelog 作為情境知識載入，否則它會繼續根據舊的參數化版本捏造語法。」

### Contextual knowledge

[代理人](#agent)可以直接從當前[脈絡](#context)中讀取的事實——使用者的任務指令、代理人已讀入的檔案、[工具結果](#tool-result)（Tool Results）、在[工作階段](#session)開始時載入的 [AGENTS.md](#agentsmd) 內容。與[參數化知識](#parametric-knowledge)（Parametric Knowledge）相對：參數化知識是從參數中*召喚*出來的；情境知識是從[視窗](#context-window)中直接*讀取*的。當代理人從情境知識出發時，[幻覺](#hallucination)（Hallucination）發生的機率大幅降低——答案就在眼前，無需從模糊的記憶中挖掘。

*只有在*與參數化知識對比時才使用此術語；其他情況直接說**脈絡**即可。

*避免使用：*「工作記憶體」——情境知識是當下在視窗裡的內容；[記憶系統](#memory-system)（Memory System）則是將跨工作階段的內容帶入其中的機制。兩者的尺度不同，不能混淆。

*使用範例：*

「為什麼我貼了 API 文件它就能對，不貼就亂說？」

「貼了文件後，它讀的是情境知識——像在翻書查答案。沒貼的時候依賴的是參數化知識，那些少見的端點就會模糊。」

### Attention relationship

在預測每個[詞元](#token)時，[模型](#model)會將[脈絡](#context)中所有其他詞元都納入考量——有些影響深遠，有些幾乎微不足道。兩個詞元之間的配對關係即為**注意力關係**（Attention Relationship），有意義的配對（例如「她」與「Sarah」，或一個 `getUser()` 呼叫與其 `function getUser` 定義）彼此的影響遠大於無關聯的配對。一個包含 N 個詞元的脈絡，大約有 N² 個注意力關係。

*使用範例：*

「它一直在 diff 裡搞混那兩個 `user` 符號——聽起來像是進了[混沌區](#smart-zone)。」

「對，每個呼叫端與其宣告之間的注意力關係互相干擾——相同的詞元形狀，但綁定的對象不同。把其中一個改名，配對關係就會變得清晰。」

### Attention budget

每個[詞元](#token)（Token）能分配給其餘[脈絡](#context)（Context）的影響力是有限的。對[某個關係](#attention-relationship)（Attention Relationship）施加大量影響，留給其他關係的就越少。這個預算是每個詞元固定的，不會隨脈絡擴大而增長，這正是為何[工作階段](#session)越長，效果越稀薄。

*使用範例：*

「它為什麼一直忽略我貼在最上面的 Schema？」

「我們已深入[混沌區](#smart-zone)了——每個詞元的注意力預算是固定的，但脈絡不斷增長。Schema 的訊號現在必須跟幾千個新詞元競爭。」

### Attention degradation

隨著[工作階段](#session)不斷增長，每個[詞元](#token)的[注意力預算](#attention-budget)（Attention Budget）必須分配給更多的競爭者。任何一個[有意義關係](#attention-relationship)（Attention Relationship）上的訊號都會減弱；不相關的[脈絡](#context)雜訊大量湧入。同樣的[模型](#model)、同樣的[參數](#parameters)——只是要從同一個盤子上餵食的嘴巴多了。這是清晰區與[混沌區效應](#smart-zone)的根本成因。

*使用範例：*

「它深陷混沌區了——憑空捏造出型別檔裡根本不存在的泛型。」

「注意力衰退（Attention Degradation）。型別定義仍在脈絡中，但它的訊號被我們後來加入的所有內容淹沒了。[清除](#clearing)並重新載入。」

### Smart zone

[工作階段](#session)剛開始時，[代理人](#agent)處於「清晰區」（Smart Zone）——思維敏銳、專注、召回能力良好。隨著工作階段增長，它逐漸漂入「混沌區」（Dumb Zone）：更粗心、更健忘、更多錯誤——且更多**忠實性[幻覺](#hallucination)**。同樣的[模型](#model)、同樣的[駕馭](#harness)——只是[脈絡](#context)變多了。這是[注意力衰退](#attention-degradation)的直觀感受。工作階段膨脹時應[清除](#clearing)或[壓縮摘要](#compaction)，不要硬撐。

*使用範例：*

「前三個元件做得完美，第四個直接毀了。」

「你已出了清晰區——同樣的模型，只是深入混沌區了。壓縮摘要並重新載入計劃，下一個元件就會順利。」

## Section 5 — 交接

### Clearing

結束當前[工作階段](#session)並啟動一個全新的工作階段。下一則訊息從空白的工作階段和空白的[上下文視窗](#context-window)重新開始。通常由使用者主動觸發。

*使用範例：*

「它陷入迴圈，一直在那個失敗的測試上打轉。」

「直接清除——帶著計劃文件和測試檔案重開一個新工作階段。繼續跟既有的[脈絡](#context)纏鬥毫無意義。」

### Handoff

將[代理人](#agent)的[脈絡](#context)從一個[工作階段](#session)轉移到另一個，且沒有返回路徑。傳遞方式各異——可以是書面的[交接文件](#handoff-artifact)（Handoff Artifact）、記憶體內的摘要（[壓縮摘要](#compaction)），或其他方式。與[清除](#clearing)（Clearing）不同——清除不進行任何轉移。進行交接的原因多樣：切換角色（規劃者→實作者）、啟動 [AFK](#afk) 執行、分散到並行工作階段，或釋放[上下文視窗](#context-window)空間。

*使用範例：*

「規劃工作階段越來越沉重——我應該繼續撐下去嗎？」

「做一次交接。把決策寫進文件，清除工作階段，然後在新的工作階段中讀取那份文件來開始實作。」

### Handoff artifact

一份作為[交接](#handoff)（Handoff）傳遞機制的文件——由一個[工作階段](#session)撰寫，供另一個工作階段讀取。這是多種傳遞方式之一（另見**壓縮摘要**，[Compaction](#compaction)）。

*使用範例：*

「如何在規劃代理人和實作代理人之間分工？」

「讓規劃者寫一份交接文件——記錄檔案路徑、決策和約束條件。實作者的工作階段從指向該文件的指針開始，以它作為任務簡報。」

### Spec

一份描述跨多個[工作階段](#session)工作的[交接文件](#handoff-artifact)（Handoff Artifact）——記錄正在構建的是什麼，而非每個工作階段如何完成各自的份額。隨著工作進展而演進。由[任務單](#ticket)（Tickets）組成。

*使用範例：*

「這些應該全放在一個工作階段裡嗎？」

「不，把它整理成規格書——拆分成任務單，每張任務單用獨立的工作階段跑。試圖在單一[脈絡](#context)裡完成整件事，還沒跑到一半就會碰到[混沌區](#smart-zone)。」

### Ticket

一份劃定單一[工作階段](#session)工作範圍的[交接文件](#handoff-artifact)（Handoff Artifact）。可以獨立存在，也可以作為[規格書](#spec)（Spec）的子項之一。任務單可以阻塞或被同層任務單阻塞，因此工作順序從它們的相依關係圖中自然浮現，而非依賴線性計劃。

*使用範例：*

「這次遷移的規格書要從哪裡開始？」

「看任務單圖——Schema 變更阻塞回填，回填阻塞 API 切換。挑一個沒有前置依賴的葉節點，然後跑一個工作階段處理它。」

### Compaction

一種在記憶體中進行的[交接](#handoff)（Handoff）：將前一個[工作階段](#session)的歷史記錄摘要化，作為新工作階段的起點。有損耗——以細節換取空間餘裕。可由使用者手動觸發，也可[自動觸發](#autocompact)。

*使用範例：*

「[脈絡](#context)越來越重，我還有測試要完成。」

「先壓縮摘要再開始——把關鍵內容寫進摘要提示詞，讓新工作階段保留 Schema 決策、捨棄探索過程的雜訊。」

### Autocompact

由[駕馭](#harness)（Harness）在[上下文視窗](#context-window)接近填滿時自動觸發的[壓縮摘要](#compaction)（Compaction）。

*使用範例：*

「它似乎不記得我們早些時候對 Schema 做的決定了。」

「自動壓縮摘要（Autocompact）在[對話輪次](#turn)之間觸發了——早期的決定被摘要化，可能有些細節遺失了。重新載入計劃文件，或者下次手動壓縮，這樣你才能控制哪些內容被保留。」

## Section 6 — 記憶與引導

### Memory system

一套試圖讓[代理人](#agent)能夠跨[工作階段](#session)[保有狀態](#stateful)（Stateful）的系統。在工作階段進行中將資訊持久化到[環境](#environment)，並在未來工作階段開始時重新載入[上下文視窗](#context-window)，使代理人在使用者[清除](#clearing)工作階段後仍能維持連續性。

*使用範例：*

「我每次都要重新告訴它我用的是 Postgres，不是 MySQL。」

「接上記憶系統——在第一個[對話輪次](#turn)把它學到的內容寫入[檔案系統](#filesystem)，並在工作階段開始時重新載入。[模型](#model)本身是[無狀態的](#stateless)；記憶層模擬了持續性。」

### AGENTS.md

一個位於[環境](#environment)（Environment）中、由[駕馭](#harness)（Harness）在[工作階段](#session)（Session）開始時載入[上下文視窗](#context-window)（Context Window）的檔案——這是專案給[代理人](#agent)的常駐任務說明書。各家駕馭通用的慣例。

*避免使用：* 將 AGENTS.md 用於應[漸進式揭露](#progressive-disclosure)（Progressive Disclosure）的內容——放在 AGENTS.md 裡的任何內容，每個[對話輪次](#turn)（Turn）都要付出[詞元](#token)（Token）代價。

*使用範例：*

「為什麼每個工作階段一開始就已燒掉 4000 個詞元了？」

「看看 AGENTS.md——有人把整份樣式指南直接貼在裡面，而不是把它放在[技能](#skill)（Skill）後面按需載入。」

### Progressive disclosure

只將[代理人](#agent)當下需要的[脈絡](#context)載入，並以指標指向其餘內容。借鑒自 UI 設計。

*使用範例：*

「我應該把整份樣式指南塞進 [AGENTS.md](#agentsmd) 嗎？」

「不——漸進式揭露（Progressive Disclosure）。把樣式指南作為一個[技能](#skill)（Skill）來引用，讓代理人在真正需要寫元件時才載入它。AGENTS.md 每個[對話輪次](#turn)都要付出[詞元](#token)代價。」

### Skill

一種可訓練的能力單元——針對某一項任務做好所需的指令和資源，存放在[環境](#environment)中，只在相關時才載入[上下文視窗](#context-window)。這是[駕馭](#harness)中實現[漸進式揭露](#progressive-disclosure)（Progressive Disclosure）的基本單位。

*避免使用：*「[工具](#tool)」——工具是代理人*呼叫*的東西；技能（Skill）是代理人*讀取*的指令。

*使用範例：*

「部署操作手冊要放哪裡？」

「作為一個技能——代理人只在任務涉及部署時才載入它。放在 [AGENTS.md](#agentsmd) 裡，每個[對話輪次](#turn)就要為一個每週只用一次的東西消耗[詞元](#token)。」

### Subagent

由另一個代理人透過[工具呼叫](#tool-call)（Tool Call）生成的[代理人](#agent)。在自己的[工作階段](#session)中、帶著自己的[上下文視窗](#context-window)運行，並回傳單一[工具結果](#tool-result)。與[交接](#handoff)（Handoff）不同——父代理人明確期待一個返回結果；交接則沒有返回路徑。**無法再生成子代理人**——這個樹結構只有一層深。子代理人的存在是為了隔離[脈絡](#context)，而非構建層級結構。

*使用範例：*

「grep 結果把我的脈絡撐爆了。」

「生成一個子代理人（Subagent）來做搜尋——它用自己的上下文視窗消耗那些雜訊，再把你真正需要的兩個檔案路徑回報給你。」

## Section 7 — 工作模式

### Human-in-the-loop

一種工作模式，一或多位人類在[工作階段](#session)進行中全程與[代理人](#agent)搭檔——即時審查、重新導向或協作。人類全程在場且主動參與，而不只是針對個別操作把關。

*使用範例：*

「要讓這個任務 [AFK](#afk) 跑一夜嗎？」

「不，這是 Schema 遷移——保持人在迴圈（Human-in-the-loop）。我想看到每個步驟，如果它選錯了要回填的欄位，我要能即時介入調整。」

### AFK

一種工作模式，使用者啟動一個[工作階段](#session)後便離開，讓[代理人](#agent)（Agent）無人監督地獨立執行。這是 AI Coding 的吞吐量倍增器——在你睡覺、吃飯或處理其他事情時，可以同時並行執行多個 AFK 工作階段。通常需要寬鬆的[權限模式](#permission-mode)（Permission Mode）搭配[沙盒](#sandbox)（Sandbox）機制才能安全運作。

*避免使用：*「背景代理人」——這個說法以機器為中心（「在背景執行」），而非以人的行為模式為中心（「使用者已離開」）。AFK 的核心事實是：使用者不在監看。

*使用範例：*

「我要讓這個工作 AFK 執行——三個沙盒化的代理人負責重構，早上再來審查 PR。」

「要[繞過權限](#agent-mode)嗎？」

「對，唯讀[檔案系統](#filesystem)，不連外網。」

### Automated check

在[環境](#environment)中執行的確定性驗證——測試、型別檢查、靜態分析（lint）、建置、pre-commit hooks。結果只有通過或失敗，不涉及判斷。這是[代理人](#agent)可以自行修正、無需任何人介入的訊號。不穩定的測試是壞掉的自動化檢查，而非不算數的檢查；自動化檢查就是要設計成確定性的。

*避免使用：*「回饋迴路」、「反壓」——這兩個詞把自動化檢查和[審查](#automated-review)混為一談。*避免使用：*「測試」——測試是自動化檢查的一種，但並非所有自動化檢查都是測試。

*使用範例：*

「代理人在 [AFK](#afk) 執行時一直交出有問題的程式碼。」

「[沙盒](#sandbox)裡接了哪些自動化檢查？」

「只有單元測試。」

「加上型別檢查和靜態分析——它在 PR 送出之前就能自行從這些結果修正。」

### Automated review

由一個[代理人](#agent)審查另一個代理人的工作，通常使用不同的[模型](#model)或[系統提示詞](#system-prompt)。非確定性的：它會形成判斷。可以在任何地方執行——合併前的 PR 審查、提交歷史的事後審查、作為[子代理人](#subagent)在工作階段中途執行。CI 裡的 LLM-as-judge（語言模型作為裁判）是自動化審查，而非[自動化檢查](#automated-check)；判斷一件事屬於哪個類別，看的是斷言*做了什麼*，而非在哪裡執行。

*避免使用：*「AI 審查」、「代理人審查」——過於模糊，無法與執行工作的代理人本身區分。

*使用範例：*

「[AFK](#afk) 執行產出了太多劣質 PR。」

「在合併前加一個自動化審查步驟——使用不同模型、獨立的系統提示詞，範圍鎖定在安全性和介面合約的變更。」

### Human review

使用者親自閱讀[代理人](#agent)生成的程式碼並形成判斷。閱讀 diff 或修改後的檔案才算數；只閱讀代理人對其操作的*描述*並不算——敘述不等於產出物本身。

*避免使用：*單獨說「程式碼審查」——這個說法含糊，無法區分是人工審查還是[自動化審查](#automated-review)。

*使用範例：*

「我人工審查了 [AFK](#afk) 的輸出。」

「你讀了 diff 還是只看摘要？」

「讀了 diff。摘要說它刪除了死碼——結果那個函式是從一個生成的檔案裡呼叫的。」

### Vibe coding

一種工作模式，使用者直接接受[代理人](#agent)的程式碼，不進行[人工審查](#human-review)。程式碼差異被視為不透明的黑盒——重要的是程式是否正常運作，而非內部有什麼。[自動化審查](#automated-review)和[自動化檢查](#automated-check)可能仍會執行；氛圍程式設計（Vibe Coding）對這兩者都保持沉默。

*避免使用：*「氛圍程式設計」作為「低品質 AI Coding」的代名詞——這個術語描述的是審查立場，而非所產生的程式碼品質。

*使用範例：*

「你有讀它在認證流程裡改了什麼嗎？」

「氛圍程式設計（Vibe Coding）了——登入還能用，我就只確認這個。」

「推送之前把 diff 讀一遍，在認證上氛圍程式設計是 secrets 洩漏進 log 的方式。」

### Design concept

使用者與[代理人](#agent)之間對於正在構建的事物所共同持有的理解，存在於雙方之間，但獨立於任何具體產出物之外。Brooks 的術語（出自《The Design of Design》）：對話、[交接文件](#handoff-artifact)（Handoff Artifacts）和程式碼，都是試圖捕捉或觸及設計概念的產出物，但它們都*不等同於*設計概念本身。設計概念的品質，可從建立它的對話品質中感受出來。

*使用範例：*

「它寫出了我要求的東西，但還是寫錯了。」

「你們還沒有建立共同的設計概念——它在用假設填補空白。在你讓它寫[規格書](#spec)之前，先持續對話，直到取消、退款和部分履行的邊界情況都在你們之間對齊為止。」

### Grilling

一種與[代理人](#agent)共同發展[設計概念](#design-concept)（Design Concept）的技術：由代理人以蘇格拉底式的方式訪談使用者，每次針對一個決策，並為每個決策提出一個建議答案。這個方式刻意放慢直奔最終計劃的衝動——在概念穩定之前，不撰寫任何[交接文件](#handoff-artifact)（Handoff Artifact）。

*使用範例：*

「它直接去寫[規格書](#spec)，結果把取消邏輯搞錯了。」

「先問答引導（Grilling）它——讓它在提交任何文字之前先問你關於部分取消、退款和時序的問題。在對話中釐清比在程式碼中修正要便宜得多。」

