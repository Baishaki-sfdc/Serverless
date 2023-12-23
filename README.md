# Serverless-Inventory Tracking System
## Scenario:
. Stores from around the world will upload an inventory file to Amazon S3. 
 Project team wants to be able to view the inventory levels and send a notification when inventory levels are low.

## Steps:
•	You will upload an inventory file to an Amazon S3 bucket.
•	This upload will trigger a Lambda function that will read the file and insert items into an Amazon DynamoDB table.
•	A serverless, web-based dashboard application will use Amazon Cognito to authenticate to AWS. The application will then gain access to the DynamoDB table to display inventory levels.
•	Another Lambda function will receive updates from the DynamoDB table. This function will send a message to an SNS topic when an inventory item is out of stock.
•	Amazon SNS will then send you a notification through short message service (SMS) or email that requests additional inventory.

