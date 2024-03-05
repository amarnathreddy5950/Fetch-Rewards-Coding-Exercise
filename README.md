# Hello, Welcome to the Fetch Rewards Coding Exercise

## Building a New Structured Data Model
Our first step is to review unstructured JSON data and diagram a new structured relational data model. To do this I represented the new data model in the relational schema of the given data. Apart from the already existing tables, I created rewardsReceiptItemList and category tables which are derived from receipts and brands tables respectively.

Note: rewardsReceiptItemList was a column in the form of a JSON array in the receipts table.

## Answers to Stakeholder questions

### Question: 
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
Average spend for receipts with 'FINISHED' status: 80.85430501930502
Average spend for receipts with 'REJECTED' status: 23.32605633802817
