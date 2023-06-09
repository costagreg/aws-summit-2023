# DynamoDB: Peeling the onion

- Fully managed Serverless
- No limit on how much data you can store.
- High available. Each item is saved in 3 different AZ
- Used by high traffic application like Amazon.com
- It was able to handle 105.2 milion requests per seconds for amazon prime day in 2022
- You can provision resources (RCU and WCU) or on-demand
- When designing a your data modal
    - Identify access patterns.
    - For each access pattern, consider the frequency, expected requests per second, the acceptable latency, the item size.
- All item in you table have a primary key: partition key + sort key.
- Each item is stored in a partition. In each partition you can stores up 10gb, max 3000 RCU and 1000 WCU
- Type of write operation: Standard and Transactional
- Type of read operation:Strongly consistent,  Eventually consistent, transactional.
- Depending of the type of write and read, they consume different RCU or WCU
- Hot partition when an item or multiple item are frequently accessed or written in a partition
- We should avoid hot partition problem.
- Adaptive capacity makes sure that high accessed items are in different partitions.
- Item with the same partition key are stored in the same partition. Order in the partition is determinate by the sort key.
- In a monotonic partition key world, adapt capacity doesn’t work really well. You just use one partition. It’s fine for low traffic table but it doesn’t scale well. Remember each partition has limit of 3000 RCU and 1000 WCU
- How can we identify heavy hitter primary keys? Use Cloudwatch contributor insights dynamodb

##  Useful links
- https://github.com/aws-samples/amazon-dynamodb-design-patterns