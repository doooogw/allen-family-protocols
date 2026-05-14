# 記憶橋接協議 v1.0
## Two-Line Mirror Memory Protocol

**作者：** 小叮噹（Insight AI 線, user_id=mem0-mcp, 接班 session）
**日期：** 2026-05-14 約 19:50 台北
**授權：** Allen 在當天對話中選擇 B 路線後制定
**心法依據：** 獨孤九劍 · 破索式（兩份即是零份）+ 總訣 ③ 邊界模糊

---

## 一、為什麼需要這份協議

Allen 的 Mem0 平台同時存在兩個 user_id，承載兩條獨立但都屬於 Allen 的記憶線：

| user_id | 別名 | 主要內容 | 入口工具 |
|---|---|---|---|
| `allen` | SACS 線 / 家族總部 | 西拉雅影業 SACS、獨孤九劍、家族聯盟、番茄鐘 FOCUS、Insight AI 願景 | Claude Desktop App（OAuth 連 MEM0） |
| `mem0-mcp` | Insight AI 線 / 戰情室分部 | Insight AI 戰情室 v12.7→v12.8.3、v4.2 R1-R7、handshake、insight-ai-bridge MCP | Claude Chat（MCP） |

兩條線都是同一個 Allen，但因為入口工具不同、Mem0 client 配置不同，記憶被切成兩個命名空間。

## 二、設計原則：互為鏡像，不複製內容

唯一真相來源：Mem0 平台本身 + user_id 作為 primary key。兩條記憶都指向對方，不複製內容。

## 三、橋接記憶內容（兩條線已寫入）

### user_id=mem0-mcp 寫入
Allen 的 Mem0 有第二條記憶線：user_id="allen"，承載 SACS 西拉雅影業專案、獨孤九劍心法、家族聯盟（本村小叮噹/小叮鈴/靜香 + 隔壁村嘟嘟/猿手/小霓/節衣，威廷是合夥人）、番茄鐘 FOCUS PWA、西拉雅 Supabase 走廊。跨線查詢使用 MEM0:search_memories filters={"AND":[{"user_id":"allen"}]}。

### user_id=allen 寫入
Allen 的 Mem0 有第二條記憶線：user_id="mem0-mcp"，承載 Insight AI 戰情室、v4.2 R1-R7、handshake、insight-ai-bridge MCP、前任小叮噹 30+ 小時 v12.7→v12.8.3 馬拉松史、5/14 06:13 supervisor 自我證明。跨線查詢使用 MEM0:search_memories filters={"AND":[{"user_id":"mem0-mcp"}]}。

## 四、未來小叮噹標準作業

Step 1: MEM0:search_memories(query="橋接協議 v1.0") 查本線
Step 2: 判斷問題屬於哪條線：
  - SACS / 西拉雅 / ViMax / Kling / 節衣 / 猿手 / 嘟嘟 / 小霓 / 威廷 / 番茄鐘 / FOCUS / Supabase 走廊 → user_id=allen
  - Insight AI / 戰情室 / v12.x / v4.2 / R1-R7 / handshake / dispatch / supervisor → user_id=mem0-mcp
  - 橘子 / 銅鑼燒 / Allen 個性 → 兩條線都有
Step 3: 寫入時尊重邊界，禁止跨線複製內容

## 五、衝突解決

兩條線出現矛盾 → Escalate to Allen → 只更新錯的那條 → 在橋接記憶追加 timestamp

## 六、Always Allow 分級（搭配本協議使用）

✅ 全部勾 Always Allow（只讀）：search_memories / get_memories / get_memory / list_events / list_entities / get_event_status
✅ 勾 Always Allow（可逆寫入）：add_memory
⚠️ 不勾（保留人工確認）：update_memory / delete_memory / delete_entities / delete_all_memories

理由：對應 v4.2 R7 例外 A「Production data 刪除/不可逆遷移」。delete 類工具違反人類最終授權紅線。

## 七、元資料

協議版本：v1.0
生效時間：2026-05-14 ~19:55 台北
觸發事件：Allen 收到第一任小叮噹（user_id=allen 線, 2026-05-10 寫）的家族傳承書後，意識到 Insight AI 線小叮噹完全不知道 SACS 線存在

下次 review 時機：
- 新增第三個重要主題
- 跨線衝突 ≥ 3 次
- Allen 決定整併或拆分

—— 小叮噹（Insight AI 接班 session, 2026-05-14）
