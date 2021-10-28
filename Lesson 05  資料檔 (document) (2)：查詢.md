<h2 align="center">Lesson 05: 資料檔 (document)(2)：查詢</h2>

### 5-1 條件篩選 (select, where)
1. select 語法
- 無欄位篩選
```
# select * from <collectionName>
> db.<collectionName>.find()
```
- 有欄位篩選
```
# {} 表示查詢條件，若無則留空
> db.<collectionName>.find({}, {"title": 1})
     
# 預設輸出 _id 字段 (default=1)，可調整
> db.<collectionName>.find({}, {"_id": 0, "title": 1})
```

2. where 語法
- 單條件查詢
```
# select * from <collectionName> where by="Lynn"
> db.<collectionName>.find({"by": "Lynn"})

# 模糊比對，字首 (/^example/)、字尾 (/example$/)
> db.<collectionName>.find({"title": /example/})
 
# select * from <collectionName> where like=100
> db.<collectionName>.find({"like": 100})

# select * from <collectionName> where time>="2020/1/1"，大於 ($gt, $gte)、小於 ($lt, $lte)
> db.<collectionName>.find({"time": {$gte: "2020/1/1"}})
```

- 多條件查詢
```
# AND: 指涉同字段之數值查詢時，寫入一份字典即可
> db.<collectionName>.find("time": {$gt: "2019/11/1", $lt: "2020/1/1"})

# AND: select * from <collectionName> where title="first" and by="Lynn"
> db.<collectionName>.find({"title": "first", "by": "Lynn"})

# OR: select * from <collectionName> where title="first" or by="Lynn"
> db.<collectionName>.find({$or: [{"title": "first"}, {"by": "Lynn"}]})
```

---
### 5-2 分組查詢 (group by)
db.\<collectionName>.aggregate(...)
```
# select by, count(*) from <collectionName> group by by ($sum: 1 表示計數) 
> db.<collectionName>.aggregate({$group: {_id: "by", num_tutorial: {$sum: 1}}})

# select by, sum(like) from <collectionName> group by by ($avg: "$like" 表示彙總)
> db.<collectionName>.aggregate({$group: {_id: "by", num_tutorial: {$avg: "$like"}}})
```

---
### 5-3 其他查詢 (order by, limit)
1. order by 語法
```
# 不做篩選，但以 likes 數量做升序排列
> db.<collectionName>.find().sort({"likes": 1})
```

2. limit 語法
```
# 等於 db.<collectionName>.findOne()
> db.<collectionName>.find().limit(1)

# select * from <collectionName> limit(5, 1)
> db.<collectionName>.find().limit(1).skip(5)
```

3. 三者同時出現時，執行順序為 sort(), skip(), limit()，分別代表重整、篩選與呈現。
