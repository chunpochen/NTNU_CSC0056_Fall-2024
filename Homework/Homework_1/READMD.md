# Software Development Assignment

此部分包含兩個練習，為了熟悉 Mosquitto 的使用和 Git 的基本操作。

## 1 監聽 Mosquitto 公開 Broker
使用 `mosquitto_sub` 程式監聽 Mosquitto 公開 broker (`https://test.mosquitto.org/`) 上的所有訊息，並截圖顯示所獲得的訊息。
### 步驟
1. 瀏覽 [test.mosquitto.org](https://test.mosquitto.org/) 網站並了解使用資訊。
2. 使用以下指令連接至公開 broker 並訂閱所有訊息：
```bash
mosquitto_sub -h test.mosquitto.org -p 1884 -t "#" -v
```
3. 截圖顯示的主題名稱及訊息內容，並將此截圖保存為證明。

## 2 修改 mosquitto_sub 以計算訊息數量
### 步驟
1. 在 `sub_client.c` 中新增一個 total_count 的全域變數：
```
int total_count = 0;
```
2. 找到呼叫 `print_message(...)` 的那一行，註解掉此行，並在其後新增以下程式碼：
```
printf ("%d ", total_count++);
```
3. 在 `client` 目錄中執行 make 指令，重新編譯程式：
```
make
```

### 產生補丁檔案
1. 使用以下指令創建補丁檔，記錄對 `sub_client.c` 的修改：
```
git diff sub_client.c > hw1.patch
```
2. 使用 `cat` 查看補丁內容，確保記錄無誤：
```
cat hw1.patch
```

#### 將產生的 `hw1.patch` 檔案作為作業提交。
#### 備註: 請確保所提交的補丁檔可以成功應用在指定的 [Mosquitto](https://github.com/wangc86/mosquitto) 程式庫。
