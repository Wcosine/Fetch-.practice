## Fetch 小練習
這是一個使用 Vue3 `script setup` 語法實作的Fetch小練習。

主要目的是為了熟悉 Fetch 的使用方法。

## 練習內容
- GET 請求：取得資料 [練習1](GET請求.vue)
- POST 請求：送資料給伺服器 [練習2](POST請求.vue)
- 錯誤處理：檢查 res.ok 狀態 [練習3](錯誤處理.vue)
- 自訂 PUT / DELETE（進階請求）

#### 啟動本機 JSON Server 假資料伺服器
1. 安裝 JSON Server： `npm install -g json-server`
2. 啟動伺服器： `json-server --watch db.json --port 3000`
3. 在 Vue 專案中請求：( 依使用需求請求 )
   - http://localhost:3000/users
   - http://localhost:3000/posts
   - http://localhost:3000/comments
