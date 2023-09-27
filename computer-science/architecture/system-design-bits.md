# System design bits

*   **Event bus:**

    E.g.: Kafka. Event-driven architecture pattern is a distributed asynchronous architecture pattern to create highly scalable reactive applications. The pattern suits every level of application stack from small to complex ones. The main idea is delivering and processing events asynchronously.

    * **Broker topology: Y**ou send events to a central broker and all subscribers of this broker receive and process events asynchronously.

    ![](<../../.gitbook/assets/image (4).png>)

    * **Notify the event to all subscribers:** Whenever the event bus receives an event from event creators, it passes the event to all subscribers. Subscribers process the event data with their own logic. Subscribers can also create new events and pass it to the event bus too. Event bus does not care about if the receiver fails to receive the event message. (Similar to Redux)
      * Replicating data to all subscribers can increase memory demand for each one of them.
      * Does not care about the assurance of the delivery.
      * Filtering should be done in subscribers
    * **Notify the event shadow to all subscribers (with a watcher):** Whenever the event bus receives any event, it saves it to an **Event Store**. Then passes the event shadow to all subscribers. Subscribers process the event shadow and fetch the event data from Event Store when they start processing.
      * Less memory consumption
      * Need to implement a read-heavy event store and an event watcher
      * Filtering should be done by subscribers
    * **Notify the Event Shadow to Filtered Subscribers:** Same as before but filtering the events before notifying the subscribers.
    * **Ordered delivery to subscribers:** In Kafka, consumers subscribe to the given list of topics to get dynamically assigned partitions and then they poll the data from the topics or partitions specified using one of the subscribe/assign APIs.
      * Increasing the number of partitions can be hard.
