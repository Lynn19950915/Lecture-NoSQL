<h2 align="center">Lesson 06: 資料檔 (document)(3)：修改、刪除</h2>

### 6-1 修改語法 (單筆)
1. db.\<collectionName>.update(...)
<pre>
# query 條件 +update 內容，若無條件則留空
> db.&lt;collectionName&gt;.update({}, {$set: {"by": "Lynn"}})
> db.&lt;collectionName&gt;.update({"title": "lecture06"}, {$set: {"by": "Lynn"}})

# nMatched=nUpserted+nModified
<i>WriteResult({"nMatched": 1, "nUpserted": 0, "nModified": 1})</i>
</pre>
2. 常用 update 參數

|  | 功能 |
| :---: | :---: |
| $set | `存在即更新、不存在則創建`，即合併 Insert/Update |
| $setOnInsert | 存在即**不操作**、不存在則創建 |
| $unset | `移除該字段 (鍵-值對)` |
| $rename | 修改字段名稱 |
| $push | 於字段中追加一個 value |
| $pull | 於字段中刪除一個 value |

3. 常用 option 參數
- upsert: 布林值，若無查詢結果則`新增資料 (結合 create)`。
- multi: 布林值，設定單次修改多筆文檔，形同 `updateMany`。
```
# 允許單值新增
> db.<collectionName>.update({}, {$set: {"by": "Lynn"}}, true, false)
# 允許多值更新
> db.<collectionName>.update({}, {$set: {"by": "Lynn"}}, false, true)
```

---
### 6-2 修改語法 (多筆)
db.\<collectionName>.updateMany(...)
<pre>
> db.&lt;collectionName&gt;.updateMany({}, {$set: {"by": "Lynn"}})
# 所有滿足條件者均修改，已形同宣告 multi=true
> db.&lt;collectionName&gt;.updateMany({"title": "lecture06"}, {$set: {"by": "Lynn"}})

# matchedCount=modifiedCount
<i>{"acknowledged": true, "matchedCount": 3, "modifiedCount": 3}</i>
</pre>

---
### 6-3 刪除語法
db.\<collectionName>.remove(...)
<pre>
# query 條件+justOne 設定
> db.&lt;collectionName&gt;.remove("by": "Lynn")
# justOne: 0，形同 deleteMany
<i>WriteResult({"nRemoved": 2})</i>

> db.&lt;collectionName&gt;.remove("by": "Lynn", justOne: true)
# justOne: 1，形同 deleteOne
<i>WriteResult({"nRemoved": 1})</i>
</pre>
