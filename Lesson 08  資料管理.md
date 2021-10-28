<h2 align="center">Lesson 08: 資料管理</h2>

### 8-1 複製與分片
1. 複製
- 是資料同步的概念，提升了數據安全與高可用性。
- 資料同步於多個服務器，具有主、從節點之分<br>
從節點透過定期論詢，掌握主節點之操作紀錄並加以同步。(mongodump 做資料備份、mongorestore 做數據恢復) 

2. 分片
- 是資料分散的概念，提升了平行處理及高吞吐量。
- 資料儲放於多個服務器，以索引做平行化管理<br>
config-server 儲存元資料及各分片之資訊，作為索引管理。(如同 file-system，zookeeper 負責管理各 chunkserver)

### 8-2 監控管理
1. mongostat: 查看系統運行狀態

2. mongotop: 追蹤系統讀寫追蹤
