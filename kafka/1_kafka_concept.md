# kafka
- <a href="#introduction">簡介</a>
- <a href="#concept">核心概念</a>
    - <a href="#topic">Topic</a>
    - <a href="#message">Message</a>
    - <a href="#broker">Broker</a>
    - <a href="#producer">Producer</a>
    - <a href="#consumer">Consumer</a>
    - <a href="#consumer-group">Consumer Group</a>
    - <a href="#partition">Partition</a>
    - <a href="#zookeeper">zookeeper</a>

  
-------------

## <div id="introduction">簡介</div>

- 分佈式消息流平臺(Stream processing)，它同時也是一款開源的基於發佈訂閱模式的消息引擎系統(Message broker)。
- 採用分散式架構，方便水平擴張，提供高吞吐量、高可靠性、可用性與擴展性，且將資料存放於硬碟空間，可以長時間保存資料。

-------

## <div id="concept">核心概念</div>

![title](images/1-1.jpg)
-------
![title](images/1-2.jpg)

- #### <div id="topic">Topic</div>
    - 對於消息的定義及分類 (類似於DB table)
    - 可對 Topic 進行 partition (hash key 或 round robin 等不同演算法)
    
- #### <div id="message">Message</div>
    - 每個 message 都屬於一個 topic，該 message 列入topic 中 partition 的列隊裡
    
- #### <div id="broker">Broker</div>
    - 儲存消息的 server，多個 Broker 即是 kafka cluster
    - kafka cluster 負責 topic 的 partition , replica 
    
- #### <div id="producer">Producer</div>
    - 消息發送者，push 消息至 broker
    
- #### <div id="consumer">Consumer</div>
    - 消息消費者，從 Kafka cluster pull message
    
- #### <div id="consumer-group">Consumer Group</div>
    - 相同群組的 consumer 共享一個 offset，意旨一個 message 只會被該群組消費一次
    - 不同的 consumer group 擁有不同的 offset，完全不影響其他的 group
    - 同一 consumer group，consumer 數量不得大於 topic partition 數量 <a href="https://www.oreilly.com/library/view/kafka-the-definitive/9781491936153/ch04.html">詳情參考</a>

- #### <div id="partition">Partition</div>
    - <a href="https://www.oreilly.com/library/view/kafka-the-definitive/9781491936153/ch04.html">他說得hen棒</a>
    
- #### <div id="zookeeper">zookeeper</div>
    - 負責 kafka cluster 的配置 (bare-metal hardware)
    - topic leader follower 的選舉
    - 紀錄 consumer or consumer group 各 topic partition 的 offset (簡而言之就是讀到哪了)
    
-------

- reference: 
    - https://medium.com/@chihsuan/introduction-to-apache-kafka-1cae693aa85e
    - https://www.readfog.com/a/1632285483296985088
    - https://www.oreilly.com/library/view/kafka-the-definitive/9781491936153/ch04.html
    - https://gitbook.cn/books/5ae1e77197c22f130e67ec4e/index.html
    

-------









