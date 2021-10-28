<h2 align="center">Lesson 10: 實例應用</h2>

### 10-1 短網址系統
1. 案例需求<br>
針對網址產生一隨機亂數短網址。

2. 應用工具
- 設定一個 key：針對特定網址 (hash)。
- hash
  - 當 user 新增 (長) 網址檢查，若為 false 則產生 value (隨機亂數網址碼)。
  - 當 user 點擊 (短) 網址檢查，若為 false 則產生 value (隨機亂數網址碼)，並重新導向。

---
### 10-2 網頁統計系統
1. 案例需求
- 查詢特定網址之總造訪次數。
- 查詢特定網址之不重複 IP 訪問次數 (人次統計)。

2. 應用工具
- 設定一個 set：針對訪問 IP(IP)、一個 key：針對特定網址 (visit)。
- IP
  - 當 user 提交 request 時，將其 IP 加入 set (自動檢查元素是否重複)。
  - SCARD: 可獲得不重複元素數量。
- visit
  - 自定義格式(如 abc.com: visit)，於每次 request 執行 INCR 增加數字。
  - GET: 可獲得特定網址 value(visit)。

---
### 10-3 即時排名系統
1. 案例需求
- user 於活動時間登入作答後，可看到自己的排名。
- 當名額已達上限，即刻顯示活動結束。

2. 應用工具
- 設計兩個 key：一個針對活動 (isOver)、一個針對個別 user(account)。
- isOver
  - 當 user 登入時檢查，若為 false 則開放回答。
  - 當 user 回答後檢查，若 account: value(排名)=300，設定 isOver=true。
- account<br>
當 user 登入時檢查，若不存在則開放回答，否則顯示 account: value(排名)。
