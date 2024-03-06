# Hello, Welcome to the Fetch Rewards Coding Exercise

## Building a New Structured Data Model
Our first step is to review unstructured JSON data and diagram a new structured relational data model. To do this I represented the new data model in the relational schema of the given data. Apart from the already existing tables, I created rewardsReceiptItemList and category tables which are derived from receipts and brands tables respectively.

Note: rewardsReceiptItemList was a column in the form of a JSON array in the receipts table.

## Answers to Stakeholder questions

### Question-3: 
When considering average spending from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?
### Query:
WITH AcceptedReceipts AS (  
    SELECT TotalSpent  
    FROM `isentropic-disk-416201.Rewards.receipts`  
    WHERE rewardsReceiptStatus = 'Accepted'  
),  
RejectedReceipts AS (  
    SELECT TotalSpent  
    FROM `isentropic-disk-416201.Rewards.receipts`  
    WHERE rewardsReceiptStatus = 'Rejected'  
)  
SELECT 'Accepted' AS status, AVG(TotalSpent) AS average_spend  
FROM AcceptedReceipts  
UNION ALL  
SELECT 'Rejected' AS status, AVG(TotalSpent) AS average_spend  
FROM RejectedReceipts;  

### Result: 
The average spend for receipts with 'Accepted' status: 80.85430501930502  
The average spend for receipts with 'Rejected' status: 23.32605633802817  

similarly, we can also answer other questions which is,

### Question-4:  
When considering total number of items purchased from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?
### Query:  
WITH AcceptedReceipts AS (  
    SELECT SUM(CAST(rril.quantityPurchased AS INT64)) AS total_items  
    FROM `isentropic-disk-416201.Rewards.rewardsReceiptItemList` rril  
    JOIN `isentropic-disk-416201.Rewards.receipts` r  
    ON r._id__oid = rril._id__oid  
    WHERE r.rewardsReceiptStatus = 'Finished'  
),  
RejectedReceipts AS (  
    SELECT SUM(CAST(rril.quantityPurchased AS INT64)) AS total_items  
    FROM `isentropic-disk-416201.Rewards.rewardsReceiptItemList` rril  
    JOIN `isentropic-disk-416201.Rewards.receipts` r    
    ON r._id__oid = rril._id__oid  
    WHERE r.rewardsReceiptStatus = 'Rejected'  
)  
SELECT 'Finished' AS status, COALESCE(total_items, 0) AS total_items_purchased  
FROM AcceptedReceipts  
UNION ALL  
SELECT 'Rejected' AS status, COALESCE(total_items, 0) AS total_items_purchased  
FROM RejectedReceipts;  

### Result:
Total number of items purchased from receipts with 'Rejected' status: 173.0  
Total number of items purchased from receipts with 'FINISHED' status: 8184.0
