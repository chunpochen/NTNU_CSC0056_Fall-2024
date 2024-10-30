# Software Development Assignment
## 1 Implementing agreeting server and its client
在 Pub/Sub 模型中，可以將伺服器實作為「訂閱者」和「發布者」的組合。在此作業中將實作一個問候伺服器，該伺服器會回覆客戶端所提交的姓名問候。

1. 伺服器端：命名為 `greet_server.c`。當接收到客戶端的訊息（如："Chun Po"）後，回覆訊息為 "Hello, Chun Po"。
2. 客戶端：命名為 `greet_client.c`。
- 發布訊息至主題 `toServer`。
- 訂閱主題 `fromServer`，以接收來自伺服器的回覆訊息。
- 客戶端僅需支援從命令列參數讀取訊息內容。

## 2 Implementing a client callback function
修改 `pub_client.c`，在接收到 QoS 1 PUBACK 控制封包時，顯示一個時間戳記。

1. 新增一個名為 `my_puback_callback` 的回調函數。
2. 新增一個名為 `mosquitto_puback_v5_callback_set` 的設置函數。
3. 當接收到來自 broker 的 PUBACK 時，呼叫 `my_puback_callback`，並在其中記錄時間戳記。
4. 在 Mosquitto 程式庫中進行修改，以建立您的回調函數和訊息處理函數的連結。
##### 提示：參考 Mosquitto 中的 `mosquitto_publish_v5_callback_set` 和 `my_publish_callback` 的實作，來了解如何建立回調函數和設置函數。

## 3 Measuring the time it takes between PUBLISH and PUBACK 
基於 2.2 的基礎，運行啟用 PUBACK 回調的發布者，發送 50 條訊息並記錄每條訊息的發布時間與 PUBACK 回應時間之間的間隔。

1. 在呼叫 mosquitto_publish_v5 前記錄發布時間戳記。
2. 在 my_puback_callback 中記錄 PUBACK 回應的時間戳記。
3. 繪製兩條 CDF 曲線：
- 一條為使用本地 broker 的情況。
- 一條為使用公共 broker (`test.mosquitto.org`) 的情況。

##### 提示：參考第 4 週課程內容中的 CDF 繪圖技術來完成此部分。

#### 參考解答 - [Solution](https://hackmd.io/PIrM41rJQkegsCExdkQL0A)
