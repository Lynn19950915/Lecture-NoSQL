<h2 align="center">Lesson 02: 數據庫 (database)</h2>

### 2-1 新增語法
1. use \<databaseName>: (若不存在則創建並) 連接至該資料庫

2. 語法規定
- 名稱限制`全為小寫`，且不含特殊字元符號。
- 系統保留之數據庫名稱
  - admin: 形同 root 數據庫，能夠以`管理員權限執行`指令。
  - local: 專用存儲本地端運行內容，數據庫`不可被複製`。
  - config: 為數據庫設定檔，紀錄元資料 (metadata) 等訊息。

---
### 2-2 查詢語法
1. db: 顯示當前連接數據庫<br>
show dbs: 顯示所有數據庫列表

2. 甫創建之數據庫雖顯示於 db，卻不出現在 show dbs 清單，`至少需加入一筆數據`。
<pre>
> use lecture02
<i>switched to db lecture02</i>
> db
<i>lecture02</i>
> show dbs
<i>admin   0.000GB
config  0.000GB
local   0.000GB</i>

> db.lecture02.insert({"name": "lecture02"})
<i>WriteResult({"nInserted": 1})</i>
> show dbs
<i>admin      0.000GB
config     0.000GB
local      0.000GB
lecture02  0.000GB</i>
</pre>

---
### 2-3 刪除語法
db.dropDatabase(): 刪除 (當前) 數據庫
<pre>
> use lecture02
<i>switched to db lecture02</i>
> db.dropDatabase()
<i>{"dropped": "lecture02", "ok": 1}</i>

> show dbs
<i>admin   0.000GB
config  0.000GB
local   0.000GB</i>
</pre>
