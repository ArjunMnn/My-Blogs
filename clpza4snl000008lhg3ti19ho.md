---
title: "Building a Serverless Node.js API with AWS and Serverless Framework"
datePublished: Sun Dec 10 2023 09:25:40 GMT+0000 (Coordinated Universal Time)
cuid: clpza4snl000008lhg3ti19ho
slug: building-a-serverless-nodejs-api-with-aws-and-serverless-framework
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702201321503/501f6766-c81d-438b-944c-19a21c5cc848.png
tags: cloud, software-development, aws, cloud-computing, serverless

---

Welcome to this comprehensive tutorial on creating a serverless Node.js API using AWS services and the Serverless Framework. In this tutorial, we'll walk through the process of setting up a serverless project, deploying it to AWS using the Serverless Framework, and testing the APIs using Postman. The project allows you to manage tasks in a DynamoDB table, demonstrating basic CRUD operations.

## Prerequisites

Before we start, make sure you have the following:

1. [Sign up](https://www.serverless.com/) on [serverless.com](https://www.serverless.com/).
    
2. Node.js and npm installed. You can download them from [nodejs.org](https://www.serverless.com/).
    
3. Serverless Framework installed globally. Run the following command:
    

```bash
npm install -g serverless
```

1. AWS IAM User credentials for deployment.
    

## Project Setup

### Step 1: Clone the Project Repository

Clone the project repository from GitHub:

```yaml
git clone https://github.com/ArjunMnn/aws-node-http-api-project-dev.git
```

### Step 2: Install Dependencies

Navigate to the project directory and install the required npm packages:

```bash
cd aws-node-http-api-project-dev
npm install
```

### Step 3: Configure AWS Credentials

Run the following command to configure your AWS credentials:

```yaml
serverless config credentials --provider aws --key YOUR_ACCESS_KEY --secret YOUR_SECRET_KEY
```

Replace `YOUR_ACCESS_KEY` and `YOUR_SECRET_KEY` with your AWS IAM User credentials.

## Serverless Configuration

The `serverless.yaml` file defines the AWS infrastructure for your serverless project. Open the `serverless.yaml` file and replace the placeholder values in the `provider` section with your specific AWS configuration.

```yaml
provider:
  name: aws
  runtime: nodejs14.x
  region: YOUR_AWS_REGION
  iamRoleStatements:
    - Effect: Allow
      Action:
        - dynamodb:*
      Resource:
        - arn:aws:dynamodb:YOUR_AWS_REGION:YOUR_ACCOUNT_ID:table/KaamKaro
```

Replace `YOUR_AWS_REGION` and `YOUR_ACCOUNT_ID` with your AWS region and account ID.

## Serverless Functions

The project consists of several functions, each handling specific API endpoints. The function code is in separate files in the `src` directory.

* `hello.js`: Handles the root endpoint and returns a welcome message.
    
* `kaamBharo.js`: Adds a new task to the DynamoDB table.
    
* `kaamDikhao.js`: Retrieves all tasks from the DynamoDB table.
    
* `kaamHatao.js`: Deletes a task from the DynamoDB table.
    
* `kaamKhatamKaro.js`: Updates the completion status of a task in the DynamoDB table.
    

## DynamoDB Table

The `serverless.yaml` file includes a DynamoDB table definition. Ensure that you have the necessary permissions to create a DynamoDB table in your AWS account.

```yaml
resources:
  Resources:
    KaamKaro:
      Type: AWS::DynamoDB::Table
      Properties:
        TableName: KaamKaro
        BillingMode: PAY_PER_REQUEST
        AttributeDefinitions:
          - AttributeName: id
            AttributeType: S
        KeySchema:
          - AttributeName: id
            KeyType: HASH
```

## Deploy the Serverless Project

Run the following command to deploy the project to AWS:

```yaml
serverless deploy
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702199748384/57fea4a2-d7e6-4ac2-89d6-80989bb56854.png align="center")

This command will package and deploy your project using AWS CloudFormation.

## Testing with Postman

Use [Postman](https://www.postman.com/) to test your APIs. Here are some sample requests:

* **GET /:** Retrieve a welcome message.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702199807451/ad87e735-339a-46f9-8f7a-f8b1bce092af.png align="center")
    
* **POST /kaam:** Add a new task to the DynamoDB table.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702199884929/21223cd6-34d3-4288-aa4f-443aa2903ef6.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702200112384/588ea903-2451-442f-b9e2-964f8925bb62.png align="center")
    
* **GET /kaam:** Retrieve all tasks from the DynamoDB table.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702199928992/87e7f83b-7f78-407f-a1c8-a138fdaf7460.png align="center")
    
* **PUT /kaam/{id}:** Update the completion status of a task in the DynamoDB table.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702199993916/4d3dec7b-f05e-4561-8ec2-68149637325f.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702200234157/321b3bcd-7033-4738-84d3-95b7e33039ae.png align="center")
    
* **POST /kaam/{id}:** Delete a task from the DynamoDB table.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702200046742/77ca8ebd-2572-4db5-aed2-3e1084aaeb80.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702200265515/be2af028-9780-483e-876e-3e33408e3015.png align="center")
    

## Conclusion

Congratulations! You've successfully created a serverless Node.js API using AWS and the Serverless Framework. This project serves as a foundation for building scalable and cost-effective serverless applications. Feel free to explore and extend the functionality based on your requirements.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Check out my [**GitHub**](https://github.com/ArjunMnn) profile.