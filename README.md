# Apache Kafka應用 - 公車即時壅擠度

### 分散式系統 Group2

107703049, [108207329](https://github.com/xoxonut), 109703003, 109703032

[110356019](https://github.com/YiChingLLin), [110356022](https://github.com/dabaoku), 110356046, [111356023](https://github.com/106306067)

## 應用介紹

## 設計概念
- producer: 每次到站時發出event:{車號, 上車人數, 下車人數}
- topic: 按車號分類
- consumer: 計算出目前公車上有幾個人

## 檔案說明
### Raw Data

### Bus

### Dashboard

## Requirement
- Kafka
- Zookeeper
- Java
- Python
- Node.js
- confluent-kafka `pip install confluent-kafka`

## Flow
1. Start Zookeeper and Kafka
    - Mac: 

    `zookeeper-server-start /opt/homebrew/etc/kafka/zookeeper.properties`

    `kafka-server-start /opt/homebrew/etc/kafka/server.properties`

2. Create Topic CLI
    - Windows: 

    `kafka-topics.sh --create --bootstrap-server localhost:9092 --topic Roosevelt --partitions 3 --replication-factor 1`

    - Mac: 

    `kafka-topics --create --bootstrap-server localhost:9092 --topic Roosevelt --partitions 3 --replication-factor 1`

3. Consumer CLI
    - Windows: 
    
    `kafka-console-consumer.sh  --topic Roosevelt --from-beginning --bootstrap-server localhost:9092 --property print.key=true `

    - Mac: 
    
    `kafka-console-consumer  --topic Roosevelt --from-beginning --bootstrap-server localhost:9092 --property print.key=true `

4. Run raw-data/sender.py

    `python sender.py`

5. Run Initialize.java (第一次執行時需初始人數)
6. Run calculator.java
7. Run Bus/Bus_server/kafka-consumer.js

    `node kafka-consumer.js`

8. Open dashboard/index.html