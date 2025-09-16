# AWS Price tracker with auto alerts

A complete serveerless price tracking tool that simulates the product prices, stores price history in dynamo db and sends reasl time alerts when the products price actrually drops below the thrshold defined by the user. The process here runs automatically every 6 hours using AWS event bridge

## Features

-  Simulates random product prices
- Stores price history in DynamoDB
-  Sends real-time email alerts via SNS service 
-  Automatically runs every 6 hours using EventBridge
-  Monitors AWS budget with alerts to prevent overspending
-  100% serverless (no EC2 or manual maintenance)

-  ## Architecture Overview

EventBridge (every 6 hours)
        │
        ▼
   Lambda Function
        │
 ┌──────┴──────┐
 ▼             ▼
DynamoDB     SNS Topic
                 │
            Email Alerts

---

## Step 4: Tech Stack used

- AWS Lambda (Python)
- AWS DynamoDB (NoSQL DB)
- AWS SNS (Simple Notification Service)
- AWS EventBridge (Scheduler)
- AWS Budgets (Billing alerts)
- boto3 (AWS SDK for Python)

## ⚙️ How It Works
1.EventBridge triggers the lambda funcn every 6 hours
2.lambda simulates random price for pre defined objects
3.If the current price price of the produc is less than or equal to the target price then an alert mail is sent via sns service
4.All price checks are stored in dynamo db for loggin and history
5.AWS budgets are setup to send alerts if spending crosses a certain threshold

Getting Started

### 1. Create the DynamoDB table
- Table name: `ProductPrices`
- Partition key: `product_id` (String)

### 2. Create the SNS Topic
- Name: `PriceDropAlerts`
- Subscribe your email and confirm the subscription.

### 3. Create the Lambda Function
- Use `boto3` to connect to SNS and DynamoDB.
- Paste your Lambda function code and set env vars if needed.

### 4. Grant IAM permissions to Lambda
- Attach `AmazonDynamoDBFullAccess` and `AmazonSNSFullAccess`

### 5. Create EventBridge Schedule
- Set to run every 6 hours.
- Choose Lambda function as target.

### 6. (Optional) Set Budget Alerts
- Go to Billing → Budgets → Set $5 alert to receive monthly usage warnings.

Screenshots
<img width="1919" height="478" alt="image" src="https://github.com/user-attachments/assets/ac33a15b-5dbf-4888-a646-43bd1cbf5314" />

<img width="1332" height="596" alt="image" src="https://github.com/user-attachments/assets/4e932e1c-bac2-4733-9f29-b1610aea16fe" />

  
<img width="1510" height="581" alt="image" src="https://github.com/user-attachments/assets/269aa074-10d8-4af8-8580-2d148496a06e" />

## Author

- **Mashak Ibrahim**
- (https://www.linkedin.com/in/mashak-ibrahim-72b104216/)
- Student @ Bauhaus-Universität Weimar






