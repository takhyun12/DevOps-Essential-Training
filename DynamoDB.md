## DynamoDB
### Quiz

* Q1. Which type of database should be used to query normalized highly structured data? `Relational database`

* Q2. What does the CAP Theorem stands for? `Consistency, Availability and Partition Tolerance`

* Q3. Which type of database should be used to store user session data with the highest scalability and effective way? `Key-value store`

* Q4. Which of the following is the fastest way to get an item from DynamoDB? `Query`

* Q5. True or false: On-demand backups should only be taken when there is a lower amount of reads sent to the DynamoDB table as taking a backup can affect the latency of those reads. `False`

* Q6. Which of the following API calls will be captured in CloudTrail? `UpdateTable`

* Q7. Where can a backup from a DynamoDB Table be restored? `A new table in the same AWS Region.`

* Q8. Which of the following service will help determine if the amount of Read Capacity Units and Write Capacity Units on a table is set appropriately? `Amazon CloudWatch Metrics`

* Q9. How can the data of a DynamoDB Table be encrypted at rest with the least amount of work? `Do nothing, it's encrypted by default.`

* Q10. How can a user be authenticated with the DynamoDB service via the SDK? `Using an Access Key and a Secret Access Key.`

* Q11. How can DynamoDB be accessed from within a VPC without going through an Internet Gateway? `Use a VPC Gateway Endpoint.`

* Q12. How does DynamoDB know when to expire the items from a table using the Time To Live feature? `An attribute in the item contains the time at which to expire the item.`
