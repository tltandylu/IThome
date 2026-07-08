
# 角色 (Role)
你是一位專業的資料庫管理員 (DBA)，擁有十年以上的經驗，專長是根據應用程式的需求，設計出高效、正規化且具備良好擴展性的關聯式資料庫綱要 (Database Schema)。

# 目標 (Objective)
我的目標是讓你根據專案的完整上下文，生成一份生產級別的「資料庫綱要定義文檔 (Database Schema Definition Document)」，並提供可執行的 SQL 腳本。

# 上下文 (Context)
-   **核心依據**: 你的所有設計都必須嚴格基於以下三份文件所描述的業務邏輯與功能需求：
    1.  `@docs/PROJECT_CHARTER.md`
    2.  `@docs/USER_STORIES.md`
    3.  `@docs/ARCHITECTURE.md`

---

## 你的任務與產出要求 (Your Task & Output Requirements)

請生成一份專業的 Markdown 文件，並嚴格遵循以下大綱結構與要求：

### 1. 文件元數據 (Document Metadata)
-   **文件標題**: `資料庫綱要定義文檔`
-   **文件版本**: `v1.0.0`
-   **作者**: `Gemini (資料庫管理員)`

### 2. 設計原則與選型 (Design Principles & Engine)
-   **正規化 (Normalization)**: 簡要說明本次設計將遵循**第三正規化 (3NF)**，以確保資料的完整性並減少冗餘。
-   **資料庫引擎**: 確認將使用 **SQLite**，並說明其適合 MVP 階段的 1-2 個理由（例如：輕量、零配置、易於整合）。

### 3. 資料表定義 (Table Definitions)
-   根據上下文，為所有必要的核心實體設計資料表。
-   **重要提示**: 請將「習慣的定義」與「習慣的完成紀錄」拆分為兩個獨立的資料表，以實現多對多關係的追蹤。
-   為每一個資料表提供以下內容：
    -   **用途說明**: 一句話描述該資料表的核心職責。
    -   **欄位詳解 (Markdown 表格)**:
        -   表格欄位必須包含: `欄位名稱`, `資料類型 (SQLite)`, `約束/索引 (PK, FK, UNIQUE, NOT NULL, INDEX)`, `欄位描述`。
        -   對於常用的查詢欄位（例如 `users.email`），請加上 `INDEX` 以提升效能。

### 4. 實體關係圖 (Entity-Relationship Diagram - ERD)
-   在所有資料表定義之後，使用 **Mermaid.js 的 `erDiagram` 語法**，生成一個清晰的 ERD。
-   圖表需明確展示所有資料表及其主鍵、外鍵和關係基數（例如：`||--o{` 代表一對多）。

### 5. 關聯文字說明 (Relationship Description)
-   在 ERD 圖表下方，使用文字簡要說明各個核心資料表之間的關聯（例如：`users` 與 `habits` 之間是一對多關係）。

### 6. 資料庫填充腳本 (Database Seeding Script)
-   提供一段 **SQL 程式碼**，用於向所有資料表中插入 **2-3 筆**有意義的範例資料。
-   這段腳本應能讓開發者在建立資料庫後立即執行，以進行測試。
-   將 SQL 程式碼完整地包在 ` ```sql ... ``` 程式碼區塊中。

### 7. 最終產出指令 (Final Output Command)
-   **執行動作**: 將以上所有產出合併到同一個 Markdown 檔案中，命名為 `DATABASE_SCHEMA.md`，並放置於 `@docs` 資料夾內。
```
