# Hello, Welcome to the Fetch Rewards Coding Exercise

## Building a New Structured Data Model
Our first step is to review unstructured JSON data and diagram a new structured relational data model. To do this I represented the new data model in the relational schema of the given data. Apart from the existing tables, I created rewardsReceiptItemList and category tables derived from receipts and brands tables, respectively.

Note: rewardsReceiptItemList was a column in the form of a JSON array in the receipts table.

## Answers to Stakeholder questions

#### Question-3: 
When considering average spending from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?

#### Result: 
The average spend for receipts with 'Accepted' status is 80.85 and 'Rejected' status is 23.32.  

Similarly,

#### Question-4:  
When considering the total number of items purchased from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?

#### Result:
The total number of items purchased from receipts with 'Accepted' status is 8184 and the 'Rejected' status is 173. 

#### Please refer to SqlQueries.pdf to find SQL Queries

## Data Quality Issues in the Data Provided
#### Please refer to EDA files attached for data quality issues


