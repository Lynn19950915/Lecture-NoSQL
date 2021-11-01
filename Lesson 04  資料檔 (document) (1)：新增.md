<h2 align="center">Lesson 04: 資料檔 (document)(1)：新增</h2>

### 4-1 新增語法 (單筆)
1. db.\<collectionName>.insert/save({...})
```
# 若數據庫名稱不為 lecture04，則視為集合表
> db.lecture04.insert({"title": "lecture04",
"text": "這是集合表中，一筆文檔的某個值",
"by": ["Lynn", "Charlie"],
"time": "2020/01/03"})
```

2. 寫入變量，再新增資料。
<pre>
> document={"title": "lecture04",
"text": "這是集合表中，一筆文檔的某個值",
"by": ["Lynn", "Charlie"],
"time": "2020/01/03"}

> db.lecture04.insert(document)
<i>WriteResult({"nInserted": 1})</i>
</pre>

---
### 4-2 新增語法 (多筆)
1. db.\<collectionName>.insertMany([{...}])
<pre>
# 可將寫入指令設為變數
> example01=db.lecture04.insertMany([{"title": "first"}, {"title": "second"}])
> example01
<i>{"acknowledged": true,
"insertedIds": [ObjectId("571a22a911a82a1d94c02337"),
ObjectId("571a22a911a82a1d94c02338")]}</i>
</pre>

2. 迴圈寫入變量，再新增資料。
```
> example02=[]
# 在符合 i<=100 條件下，逐次遞加並以字典寫入變量
> for(i=1; i<=100, i++){example02.push({num: i})}
　
> db.lecture04.insert(example02)
```

3. 語法規定
- 名稱`區分大小寫`，且不得含特殊字元符號。
- 數據庫下之各文檔，字段 (鍵) 無須相同，鍵-值型態也無須統一。
<pre>
注意：但對於單一文檔，字段 (鍵) 不可重複，且具備順序性。
</pre>
