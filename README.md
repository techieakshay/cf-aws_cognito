# AWS Cognito Deployment with CloudFormation

## Overview
This CloudFormation template deploys an **Amazon Cognito User Pool** that supports authentication via **mobile, email, or username**, along with configurable properties and secrets output.

## Prerequisites
Ensure you have the following before deploying:
- **AWS CLI** installed and configured
- **CloudFormation permissions**
- **Valid domain for Cognito Hosted UI** (if required)

## Deployment Steps
### 1. Create the CloudFormation Stack
```sh
awsDeploy % aws cloudformation create-stack --stack-name appcognitoclient --template-body file://cftemplate.json --capabilities CAPABILITY_NAMED_IAM --profile local
```

### 2. Update the Stack (if needed)
```sh
awsDeploy % aws cloudformation update-stack --stack-name appcognitoclient --template-body file://cftemplate.json --capabilities CAPABILITY_NAMED_IAM --profile local
```

### 3. Delete the Stack (Cleanup)
```sh
aws cloudformation delete-stack --stack-name appcognitoclient
```

## Configuration
This template includes configurable parameters for:
- **Authentication types** (mobile, email, username)
- **Password policies**
- **User Pool name and attributes**
- **OAuth settings** (if applicable)

## Outputs
Once deployed, the stack provides:
- **User Pool ID**
- **Client App ID**
- **Secret Key** (if enabled)
- **Cognito Domain (if configured)**

Use the following command to fetch outputs:
```sh
aws cloudformation describe-stacks --stack-name appcognitoclient --query "Stacks[0].Outputs"
```

## Example JSON Output
```json
{
  "UserPoolId": "us-east-1_abc123xyz",
  "AppClientId": "xyz789abc456",
  "AppClientSecret": "somesecretkey123",
  "CognitoDomain": "https://my-app.auth.us-east-1.amazoncognito.com"
}
```

## Notes
- Ensure proper IAM permissions for CloudFormation execution.
- Modify the template for additional user attributes.

---

**Author:** Your Name  
**License:** MIT  
