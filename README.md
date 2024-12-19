# Serverless Registration Form

This project demonstrates how to create a serverless registration form using AWS services, including DynamoDB, Lambda, and API Gateway.

## Steps to Set Up the Project

### Step 1: Create a DynamoDB Table
1. Navigate to the **DynamoDB Console**.
2. Create a new table with the following details:
   - **Table Name**: `registration-table`
   - **Partition Key**: `email` (String)

### Step 2: Create an IAM Role for the Lambda Function
1. Go to the **IAM Console**.
2. Create a new role with the following details:
   - **Role Name**: `RegistrationFormRole`
   - Attach the following permissions:
     - `CloudWatchFullAccess`
     - `AmazonDynamoDBFullAccess`

### Step 3: Create the Lambda Function
1. Go to the **Lambda Console**.
2. Create a new function with the following details:
   - **Function Name**: `registration-form-function`
   - **Runtime**: Python 3.9
   - Attach the `RegistrationFormRole` created in Step 2.

### Step 4: Write the Lambda Function
Write the code for your Lambda function to handle registration form submissions and store data in DynamoDB. Ensure the function validates input data and inserts it into the `registration-table`.

### Step 5: Create an API Gateway and Enable CORS
1. Navigate to the **API Gateway Console**.
2. Create a new API to trigger the Lambda function.
3. Configure the API Gateway to enable CORS:
   - **Headers**:
     - `Access-Control-Allow-Origin: '*`
     - `Access-Control-Allow-Headers: Content-Type,X-Amz-Date,Authorization,X-Api-Key,X-Amz-Security-Token`
   - **Methods**: `POST`

### Step 6: Test the Project
1. Deploy the API Gateway.
2. Test the registration form by sending a POST request to the API endpoint with sample registration data.
3. Verify that the data is successfully inserted into the DynamoDB table.

## Technologies Used
- **AWS Lambda**: Serverless compute service to run the backend logic.
- **Amazon DynamoDB**: NoSQL database to store registration data.
- **API Gateway**: To expose the Lambda function as a RESTful API.

## Additional Notes
- Ensure all AWS resources are in the same region.
- Use environment variables in your Lambda function for better security and configurability.
- For production, restrict API Gateway access and configure IAM permissions following the principle of least privilege.