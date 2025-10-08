# SQL 技能練成

在這個課程中，將一步一步練習與學習 SQL 技能，提升技能等級至專業。
此系列筆記為參考以下 Udemy 課程人工編寫而成，建議購買相關課程，本筆記僅以實作為主：

- 講師：Nikolai Schuler 
- 課程：Master SQL in just 15 days from Basics to Pro by working daily on real-life projects

# 配置

＊本系列筆記練習皆使用 docker 配置，並預設學員已熟練最基本的 docker 技能，若不習慣可以直接安裝對應作業系統的原生執行檔。
＊本課程採用 PostgreSQL，原因在於它是最貼近標準 SQL 的資料庫（沒有資料庫與標準 SQL 完全一致，但 PostgreSQL 是最貼近的），很容易切換到其他資料庫。
＊本課程採用 pgAdmin 作為環境管理工具，可以方便地管理和管理 PostgreSQL 的資料庫。


1. 解壓縮 `learning_data/pagila-master.zip`，得到 `pagila-insert-data.sql` 檔案。
2. 建立 `sql_scripts` 資料夾
3. 將 `pagila-insert-data.sql` 檔案剪下貼到 `sql_scripts` 資料夾中。
4. 執行 `docker-compose up -d`
5. 解壓縮其餘的壓縮檔 `learning_data/*.zip`，得到其他 `.sql` 檔案。
6. 將這些檔案剪下貼到 `psql_scripts` 資料夾中。
5. 進入 `http://localhost:5050`，利用 `docker-compose.yml` 設定的帳號密碼登入 `pgadmin`
6. 連線到資料庫，`host` 為 `postgres`，帳號密碼請參考 `docker-compose.yml`
7. 完成配置，開始練習！

**NOTE**: 進入中級階段前，請先閱讀**基礎階段**的最後一個筆記的章節挑戰。

# 行前說明

1. 一但配置完成，可以在 `<db_name>/Schemas/public` 選單上按滑鼠右鍵，點擊 `Query Tool`，進入 SQL 查詢介面，先輸入 
    ```sql
    ALTER DATABASE learningdb SET timezone TO 'Europe/Berlin';
    ```
    設定時區後就可以開始練習了。
2. SQL 一般習慣欄位名稱以小寫為主，並以 `_` 連接，例如 `first_name`，而非 `firstName`，此稱為**底線式命名法**。
3. 在 SQL 中，語句格式或大小寫不影響結果，但是約定俗成的格式可以增強可讀性。
4. 在 SQL 中，與程式語言不同，Index 由 `1` 開始編號，不是 `0`。
5. 許多查詢使用 `column_index` 也可以，但非常不推薦這樣做，因為會導致失去可讀性，因此本系列筆記僅使用 `column_name`。
6. 有些題目為講師在 UDEMY 課程上提供的練習題，表內容與 `pagila-master` 不同，因此在本地環境下有些題目無法實際練習，僅需確認自己的 SQL 語句是否與答案相似即可。