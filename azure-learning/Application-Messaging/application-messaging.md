# Azure Storage Queues
- Under a Storage Account we have an option select is Queues to talk in a Asynchronous manner
- Its a way of you to store small bits of data for another application to read by creating a queue under storage account
- once created Queue has a URL, to access it we must have a Access key
- messages are short like 64 KB
- Once a message is available to read, application reading it Dequeues the message
- Some of the Azure SDK's available to read these queues are as below
    a. Microsoft.Azure.Storage.Queue
      - allows to peek messages with 30 seconds default period


# Service Bus Queue
- Cloud messaging service providing queues and topics with publish/subscribe semantics and rich features
- Fully managed service in multi or single tenant configurations with no servers to manage or licenses to buy
- More features , More expensive
- is added under a resource group
- uses namespaces
- has a max message size based on pricing tier
    Basic - 256 KB
    Standard - 256KB with Topics
    Premium - 100 MB with Topics,Messaging ops.fixed pricing
- we can choose the TLS version
- we get a SLA with Service Bus queue
- has a URL that can be accessed via REST API 
