<h2 align="center">Lesson 03: 集合表 (collection)</h2>

### 3-1 新增語法
1. db.createCollection(name, options)

2. 語法規定
- 名稱限制`全為小寫`，且不含特殊字元符號。
- 常用 option 參數

  |  | 型別 | 功能 |
  | :---: | :---: | :---: |
  | capped | 布林值 | 創建固定大小 (size) 之集合 |
  | autoIndexId | 布林值 | 自動於 \_id 建立索引 (default=false) |
  | size | 數值 | 設定集合之`大小上限` (單位為 KB) |
  | max | 數值 | 設定集合之`檔案數量上限` |

```
# 錯誤，capped 必須指定集合大小
> db.createCollection("lecture03", {capped: "true", max: 1000})
# 會先檢查 size，再檢查 max 上限
> db.createCollection("lecture03", {capped: "true", size: 30000, max: 1000})
```

---
### 3-2 查詢語法
1. show collections/tables: 顯示所有集合表列表

2. 不同於數據庫，collection 就算無數據亦會顯示於列表；亦可透過`新增資料主動創建 collection`。
```
# 數據庫新增資料語法相同，故其名稱不可為 example01
> db.example01.insert({"name": "lecture03"})
> show collections
lecture03
```

---
### 3-3 刪除語法
db.\<collectionName>.drop(): 刪除(當前)集合表
```
> use lecture03
switched to db lecture03
> show tables
example01
> db.example01.drop()
true
> show tables
```
