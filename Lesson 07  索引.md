<h2 align="center">Lesson 07: 索引</h2>

### 7-1 新增語法
1. db.\<collectionName>.createIndex(...)
```
# 以 title 升序建立索引
> db.<collectionName>.createIndex({"title": 1}}

#複合索引
> db.<collectionName>.createIndex({"title": 1, "by": -1})
```
2. 常用 option 參數
- unique: 布林值，建立`唯一索引 (即 primary key)`。
- background: 布林值，於後台建立索引 (避免影響前台運行)。

---
### 7-2 查詢語法
1. db.\<collectionName>.getIndexes: 顯示`所有集合索引列表`

2. db.\<collectionName>.totalIndexSize: 顯示集合索引大小

---
### 7-3 刪除語法

1. db.\<collectionName>.dropIndex("\<indexName>"): 刪除集合指定索引

2. db.\<collectionName>.dropIndexes(): 刪除集合`所有指引`
