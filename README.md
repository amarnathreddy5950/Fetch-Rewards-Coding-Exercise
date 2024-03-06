# Hello, Welcome to the Fetch Rewards Coding Exercise

## Building a New Structured Data Model
Our first step is to review unstructured JSON data and diagram a new structured relational data model. To do this I represented the new data model in the relational schema of the given data. Apart from the already existing tables, I created rewardsReceiptItemList and category tables which are derived from receipts and brands tables respectively.

Note: rewardsReceiptItemList was a column in the form of a JSON array in the receipts table.

## Answers to Stakeholder questions

### Question-3: 
When considering average spending from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?

### Result: 
The average spend for receipts with 'Accepted' status is 80.85 and 'Rejected' status is 23.32.  

similarly, we can also answer other question which is,  

### Question-4:  
When considering the total number of items purchased from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?

### Result:
Total number of items purchased from receipts with 'Accepted' status is 8184 and 'Rejected' status is 173. 

you can find the queries attached in SqlQueries.pdf

## Data Quality Issues in the Data Provided


