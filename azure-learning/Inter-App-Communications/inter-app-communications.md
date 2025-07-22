# Inter App Communication that are non-asyncronous
-- to keep communication real-time - we need to open channel.
-- However for Asynchronous in Azure, we have 2 choice
    a. Event
    b. Message

Diff between the 2 is message has data and fully readable without clicking etc and an event is just a notification

# Event solutions in Azure 
 a. Event Grid
    - messaging platform for events
    - in azure portal we dont create a resource to use it
    - it is available as a service, searcable in top bar
    
    i. MQTT events - used by IoT systems
    ii. Azure service events
        - subscribe to these events published by azure services
        - System topic - refer list of services that supports these events - https://learn.microsoft.com/en-us/azure/event-grid/system-topics
        - 

    iii.Custom events
        - If you want to use the event grid for custom application and have other subscribe to its events we can use this option
        - for example if you had a blod storage and wanted to create events whenever a file is modified and want to notify the change, we can create custom event for it.
 b. Event Hub
     - typically done with streaming
     - as data is coming in it just sent ahead without waiting , process as it is generated
     - recommended message broker when working with steams and large volumes of data
     - low latency
     - appened to end of stream and ordered
     - makes data available on a poll model
     - apps can poll the stream and move forward or backward in the stream
     - handles partitioning
     - already works with Kafka
     - it has a namespace name and has to be unique
     - pricing is per throughput unit per month
     - we can indicate the TLS version
     