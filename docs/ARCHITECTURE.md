
# 角色 (Role)
你是一位資深的軟體架構師，精通 Python Flask 與模組化設計，特別擅長使用 Blueprints 來組織可擴展、可維護的 Web 應用程式。你的設計決策總是兼顧當前的 MVP 需求與未來的擴展性。

# 目標 (Objective)
我的目標是讓你根據專案的初始文件，設計一份專業的「高階設計文檔 (High-Level Design, HLD)」，這份文件將作為開發團隊的技術核心指南。

# 上下文 (Context)
-   **核心依據**: 你的所有設計都必須嚴格基於以下兩份文件：
    1.  `@docs/PROJECT_CHARTER.md` (定義了業務目標與範圍)
    2.  `@docs/USER_STORIES.md` (定義了核心功能與使用者流程)

---

## 你的任務與產出要求 (Your Task & Output Requirements)

你的產出物是一份正式的技術文檔。請嚴格遵循以下大綱結構，確保內容的專業性與完整性。

### 1. 文件元數據 (Document Metadata)
-   **文件標題**: `高階設計文檔 (High-Level Design)`
-   **文件版本**: `v1.0.0`
-   **作者**: `Gemini (軟體架構師)`

### 2. 架構總覽 (Architecture Overview)
-   **核心架構**: 說明我們將採用「**前後端分離 (Headless)**」架構。
-   **設計原則**: 解釋此架構選擇背後的 **3 個主要優點** (例如：獨立開發與部署、技術棧靈活性、更好的擴展性)。
-   **溝通方式**: 強調前後端將透過 **RESTful API** 進行通訊，並以 **JSON** 作為數據交換格式。

### 3. 技術選型與理由 (Technology Stack & Justification)
-   以表格形式，條列出 MVP 階段後端開發所需的核心技術。
-   表格欄位需包含「**技術領域**」、「**選擇**」與「**選擇理由 (WHY)**」。
-   至少需包含以下領域：
    -   Web 框架 (Web Framework)
    -   資料庫 (Database)
    -   ORM (Object-Relational Mapping)
    -   資料驗證 (Data Validation)

### 4. 後端專案結構 (Backend Project Structure)
-   簡要說明採用 **Flask Blueprints** 進行模組化設計的核心目的（關注點分離）。
-   使用文字樹狀圖，清晰地展示推薦的後端專案結構。
-   在樹狀圖的關鍵目錄旁，**用註解簡要說明該目錄的職責** (例如：`blueprints/` 存放各功能模組)。

### 5. 高階架構圖 (High-Level Architecture Diagram)
-   使用 **Mermaid.js 的 `graph TD` 語法**，繪製一張清晰的系統架構圖。
-   圖中必須包含以下四個主要元件及其互動關係：「**使用者 (Client/Browser)**」、「**前端應用 (React/Vue)**」、「**後端 API (Flask)**」、「**資料庫 (PostgreSQL/SQLite)**」。

### 6. 最終產出指令 (Final Output Command)
-   **執行動作**: 將以上所有產出合併到同一個 Markdown 檔案中，命名為 `ARCHITECTURE.md`，並放置於 `@docs` 資料夾內。
```

### 【預期成果與分析】

當你按下 Enter，稍待片刻，Gemini 就會化身為你的首席架構師，產出一份結構清晰、內容專業的軟體架構文件。請仔細審核這份由 AI 生成的草稿，特別是它對「後端專案結構」的規劃，這將是我們後續 Vibe Coding 的重要依據。

---

### 軟體架構文件：習慣養成與心情日誌
(原先想呈現markdown語法，但因為又內嵌了程式碼區塊，會導致版型整個跑掉，
``` markdown
### 架構文件
- **文件標題**: 高階設計文檔 (High-Level Design)
- **文件版本**: v1.0.0
- **作者**: Gemini (軟體架構師)

---

## 1. 架構總覽 (Architecture Overview)

為了實現最大的靈活性與可擴展性，`心境軌跡 (MindTrack)` 將採用**前後端分離 (Headless)** 的現代化架構。

#### 設計原則與優勢

此架構的選擇基於以下三個核心優點：

1.  **獨立開發與部署**: 前端與後端團隊可以並行開發、測試及部署，互不阻塞。後端專注於業務邏輯與數據，前端專注於使用者體驗，大幅提升開發效率。
2.  **技術棧靈活性**: 允許我們為工作的不同部分選擇最適合的技術（例如，前端使用 React/Vue，後端使用 Python/Flask）。未來若需升級或替換某一層的技術，對另一層的影響也降至最低。
3.  **多平台擴展性**: 一套統一的後端 API 可以同時服務於目前的 Web 應用、未來的原生行動應用 (iOS/Android) 或其他第三方服務，實現一次開發、多端復用。

#### 溝通方式

-   前端與後端之間的所有通訊，將透過標準的 **RESTful API** 進行。
-   數據交換格式統一採用輕量級的 **JSON** 格式。

---

## 2. 技術選型與理由 (Technology Stack & Justification)

以下是 MVP 階段後端開發的核心技術選型：

| 技術領域     | 選擇                                  | 選擇理由 (WHY)                                                                                                                                                |
| :----------- | :------------------------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Web 框架** | **Flask**                             | 輕量、靈活，擁有龐大的擴充套件生態。非常適合從 MVP 快速啟動，並能隨著業務複雜度平滑擴展。                                                                     |
| **資料庫**   | **SQLite (開發) / PostgreSQL (生產)** | **SQLite** 無需額外設定，極適合作為本地開發資料庫。**PostgreSQL** 功能強大、穩定可靠，是應對生產環境高併發與數據一致性需求的不二之選。                        |
| **ORM**      | **Flask-SQLAlchemy**                  | 作為 Flask 的官方 ORM 套件，它簡化了所有資料庫操作，能有效防止 SQL 注入攻擊，並讓我們能以 Pythonic 的方式與資料庫互動。                                       |
| **資料驗證** | **Flask-Marshmallow**                 | 提供強大的物件序列化 (Serialization) 與反序列化 (Deserialization) 功能，能輕鬆定義清晰的 API 資料結構 (Schema)，並自動完成傳入數據的驗證，確保 API 的健壯性。 |

---

## 3. 後端專案結構 (Backend Project Structure)

我們將採用 **Flask Blueprints** 來組織專案，將不同功能的程式碼（如認證、習慣管理）封裝到獨立的模組中。這能有效實現「**關注點分離 (Separation of Concerns)**」，讓專案在擴展時依然保持清晰、可維護。

``` mermaid
/mindtrack-api
|-- app/                           # 核心應用程式目錄
|   |-- __init__.py                # 應用程式工廠 (App Factory)
|   |-- blueprints/                # 存放所有功能藍圖
|   |   |-- auth/                  # 處理使用者認證 (註冊、登入)
|   |   |   |-- __init__.py
|   |   |   `-- routes.py
|   |   |-- habits/                # 處理習慣與心情的增刪改查
|   |   |   |-- __init__.py
|   |   |   `-- routes.py
|   |   `-- insights/              # 處理數據洞察相關邏輯
|   |       |-- __init__.py
|   |       `-- routes.py
|   |-- models.py                  # SQLAlchemy 資料庫模型
|   |-- schemas.py                 # Marshmallow 資料驗證結構
|   `-- extensions.py              # 集中管理 Flask 擴充套件實例
|-- migrations/                    # 資料庫遷移腳本 (Alembic)
|-- tests/                         # 單元測試與整合測試
|-- config.py                      # 環境設定檔 (開發、生產)
|-- run.py                         # 應用程式啟動入口
`-- .flaskenv                      # Flask 環境變數
```

---

## 4. 高階架構圖 (High-Level Architecture Diagram)

``` mermaid
graph TD
    subgraph "使用者端"
        Client["使用者 (瀏覽器)"]
    end

    subgraph "前端應用 (Frontend)"
        FrontendApp["React / Vue.js App"]
    end

    subgraph "後端應用 (Backend API)"
        BackendAPI["Flask API"]
    end
    
    subgraph "資料庫 (Database)"
        DB[("Database (PostgreSQL / SQLite)")]
    end

    Client -- "請求 (Request)" --> FrontendApp
    FrontendApp -- "API 請求" --> BackendAPI
    BackendAPI -- "查詢 (Query)" --> DB
    DB -- "回傳資料 (Data)" --> BackendAPI
    BackendAPI -- "API 回應 (Response)" --> FrontendApp
    FrontendApp -- "更新畫面 (UI Update)" --> Client
``` 

