# Serverless-Inventory Tracking System
## Scenario:
Stores from around the world will upload an inventory file to Amazon S3. 
Project team wants to be able to view the inventory levels and send a notification when inventory levels are low.
## AWS Services used:
S3,DynamoDB,Lambda,SNS
## Benefits:
AWS Lambda code can run without needing to pre-allocate servers. With Lambda, you only need to provide the code and define a trigger. The Lambda function can run when it is needed, whether it is once per week or hundreds of times per second. You only pay for what you use. With Lambda, you only need to provide the code and define a trigger. The Lambda function can run when it is needed, whether it is once per week or hundreds of times per second. You only pay for what you use.<br>
This is a serverless solution that automatically scales when it is used. It also incurs little cost when it is in use. When it is idle, there is practically no cost because will you only be billed for data storage.
## IAM Role & Permissions

## Steps:
• upload an inventory file to an Amazon S3 bucket.<br>
•	This upload will trigger a Lambda function that will read the file and insert items into an Amazon DynamoDB table.<br>
•	A serverless, web-based dashboard application will use Amazon Cognito to authenticate to AWS. The application will then gain access to the DynamoDB table to display inventory levels.<br>
•	Another Lambda function will receive updates from the DynamoDB table. This function will send a message to an SNS topic when an inventory item is out of stock.<br>
•	Amazon SNS will then send you a notification through short message service (SMS) or email that requests additional inventory.<br>

## Task 1:Creating a Lambda function to load data
Lambda function will process an inventory file. The Lambda function will read the file and insert information into a DynamoDB table.
## Task 2: Configuring an Amazon S3 event
Stores from around the world provide inventory files to load into the inventory tracking system. Instead of uploading their files via FTP, the stores can upload them directly to Amazon S3. They can upload the files through a webpage, a script, or as part of a program. When a file is received, it triggers the Lambda function. This Lambda function will then load the inventory into a DynamoDB table.
## Task 3: Testing the loading process
upload an inventory file, then check that it loaded successfully.
## Task 4: Configuring notifications
notify inventory management staff when a store runs out of stock for an item. For this serverless notification functionality, you will use Amazon SNS.
## Task 5: Creating a Lambda function to send notifications
You can modify the existing Load-Inventory Lambda function to check inventory levels while the file is being loaded. However, this configuration is not a good architectural practice. Instead of overloading the Load-Inventory function with business logic, you will create another Lambda function that is triggered when data is loaded into the DynamoDB table. This function will be triggered by a DynamoDB stream.
## Task 6: Testing the System
upload an inventory file to Amazon S3, which will trigger the original Load-Inventory function. This function will load data into DynamoDB, which will then trigger the new Check-Stock Lambda function. If the Lambda function detects an item with zero inventory, it will send a message to Amazon SNS. Then, Amazon SNS will notify you through SMS or email.



 



