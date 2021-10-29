<h2 align="center">Lesson 01: MongoDB 101</h2>

### 1-1 MongoDB 簡介
1. MongoDB 為`分散式文件儲存導向`之資料庫，文件均由`鍵-值 (key-value)` 結構組成。

2. 支援多種表達式及編程語言，且可透過複製、分片提升可用性及延展性。

3. 基本名詞概析

|  | 組成 | 備註 |
| :---: | :---: | :---: |
| `數據庫 (database)` | 一至多張`集合表 (collection)` | |
| `集合表 (collection)` | 一至多筆`資料檔 (document)` | 除 capped collection 之外，不具備固定之結構 |
| `資料檔 (document)` | 一至多組`鍵-值對 (key-value)` | 鍵-值對`不可重複、有順序性`，其字段對應到 column (行) |
| 元資料 (metadata) | 系統管理資料 | 儲存於 \<dbname>.system 中 |

---
### 1-2 MongoDB 安裝
1. 資料庫創建
- 連接法：透過手動創建檔案，設定連結。
```
(terminal)
> cd c:\
> mkdir data
> cd data
# data 目錄下之 db 目錄，才是數據儲存位置
> mkdir db

# 建立連結
> C:\mongodb\bin\mongod\ --dbpath c:\data\db
> C:\mongodb\bin\mongo.exe
```
- 配置法：透過管理檔之配置，啟動連結。
```
(terminal)
> mkdir c:\data\db
> mkdir c:\data\log

(創建檔案 c:\mongodb\mongod.cfg)
systemLog:
destination:file
path c:\data\log\mongod.log
storage:
# 建立連結
path c:\data\db

> C:\mongodb\bin\mongod.exe --config "C:\mongodb\mongod.cfg" --install
```

2. MongoDB 啟動<br>
直接執行 `C:\mongodb\bin\mongod.exe`，即可進入後台管理 shell。

- 標準連線語法
```
> mongodb://[username:password@]host1[:port1][,host2[:post2]...][/[database][?options]]
```
- 連線實例
```
# 連線至本地端
> mongodb://localhost
# 以帳號、密碼連線至本地資料庫 (default=test)
> mongodb://Lynn:19950915@localhost/MongoDB
> mongodb://Lynn:19950915@localhost:27017, localhost:27018, localhost:27019
# 亦可連接至其他服務端
> mongodb://Lynn:19950915@example.com:27017, example.com:27018, example.com:27019
```
