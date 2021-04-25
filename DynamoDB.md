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

* Q17. Which of the following is a type of NoSQL Database? Select two. `Key-value store` `Document database`

* Q18. Which of the following can be added or changed after the creation of a DynamoDB table? `Global Secondary Index`

* Q19. Which of the following are part of the mandatory parameters when creating a DynamoDB table via the SDK with the on-demand read/write capacity mode? Select two. `Partition Key name` `Table name`

* Q20. The metric of ConsumedReadCapacityUnits is currently much lower than the Read Capacity Unit provisioned on a DynamoDB table. However, users are saying that they are receiving an error message of ProvisionedThroughputExceededException. What could be the issue? `The queries aren't uniformly distributed across all logical partition keys in the table.`

* Q21. Which of the following AWS service will help determine latency issues per query in DynamoDB? `AWS X-Ray`

* Q22. What are the two types of read/write capacity modes for processing reads and writes on your tables? Select 2. `Provisioned` `On-demand`

* Q23. How many Scan queries need to be sent to DynamoDB to get all the items from the table if the table contains 10 items each with 200KB of data? `2`

* Q24. A DynamoDB table is made up of a Partition Key of UserID, a Sort Key with the date and time and an attribute of Score providing the list of all the scores for a game. A dashboard needs to display the 5 highest scores from the table. What is the most efficient way to keep this dashboard in real time? `Use DynamoDB Stream and AWS Lambda to update the dashboard each time a higher score is added.`

* Q25. How can the permissions of a user be restricted only query specific attributes with the least amount of work? `Configure an Identity and Access Management Policy and apply it to the User.`

* Q26. Which of the following statement is FALSE concerning secondary indexes in DynamoDB? `Local and Global Secondary Indexes are synchronously updated when the main table is updated.`

* Q27. What feature of DynamoDB is necessary to make use of Optimistic Locking? `Conditional writes`

* Q28. Given a table that has a Partition Key of UserID, an attribute named AccountLocked and many other attributes. The AccountLocked attribute is set to TRUE when the UserID is has its account locked and isn't set when it's not locked. Not many accounts are typically locked at a time compared to the hundreds of thousands of users in that table. What would be the most optimal way to get a list of all UserID that have their account locked (AccountLocked set to TRUE)? `Create an index with UserID as the Primary Key and AccountLocked as the Sort Key. Send a Scan to the index to find the list of account locked.`



