[代理人](./Agent.md)讀取、寫入、並在其中執行程式的檔案與目錄樹——coding agent 預設的[環境](./Environment.md)類型。[AGENTS.md](./AGENTS.md.md)、[技能](./Skill.md)（Skills）、原始碼、建置腳本和[工具](./Tool.md)配置，全都存放在檔案系統中。當一個[框架](./Harness.md)「從你的專案啟動」時，它就是在將代理人指向一個檔案系統。

*使用範例：*

「它為什麼沒有讀到我的 AGENTS.md？」

「它跑的是另一個檔案系統——[沙盒](./Sandbox.md)掛載了上層目錄，而不是專案根目錄。重新指定框架的路徑。」
