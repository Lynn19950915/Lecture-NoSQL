<h2 align="center">Lesson 09: Redis 101</h2>

### 9-1 Redis簡介
1. Redis 也是鍵值資料庫，特色為`仰賴記憶體`儲存，`容量小但速度極快`。

2. 資料管理
- 與 MongoDB 一樣，均透過工作紀錄搭配`定期快照 (snapshot)`，確保資料維護。
- 亦可藉由複製、分片提升可用性與延展性。

---
### 9-2 資料型別
1. 單層結構

|  | 順序性 | 元素可重複 | 常用指令 |
| :---: | :---: | :---: | :--- |
| strings | Ｘ | Ｏ | SET (設定 key 值)、GET (取出 key 值)、INCR/INCRBY (增加)、DECR/DECRBY (減少) |
| sets | Ｘ | Ｘ | SADD (寫入元素)、SCARD (讀取元素) |
| lists | Ｏ | Ｏ | LPUSH/RPUSH (左／右側寫入)、LSET (設定項值)、LRANGE (讀取元素) |

2. 雙層結構

|  | 順序性 | 元素可重複 | 常用指令 |
| :---: | :---: | :---: | :--- |
| hashes | Ｘ | Ｏ | HSET (設定雙層 key 值)、HGET (取出多層 key 值) |
| sorted sets | Ｏ | Ｘ | |
