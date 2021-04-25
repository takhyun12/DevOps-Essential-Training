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

* Q13. Using Optimistic Locking, the user is responsible for managing the version of an item using an attribute. `True`

* Q14. When querying a DynamoDB Local Secondary Index that doesn't have a required attribute specified in the query, what is the most optimal way to get the data if that attribute is rarely needed? `DynamoDB will return the attribute from the main table if it can't find it in the index.`

* Q15. Where should large attribute values should be stored in relation to DynamoDB? `Amazon Simple Storage Service`

* Q16. Which of the following statement is TRUE concerning Amazon DynamoDB Accelerator (DAX)? `DAX should be used for an application reading from the same partition key very often.`
