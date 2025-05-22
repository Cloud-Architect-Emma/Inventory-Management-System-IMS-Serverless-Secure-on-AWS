# Inventory Management System (IMS) – Serverless & Secure on AWS
A fully serverless, scalable, and secure Inventory Management System built using AWS. This system enables businesses to manage product inventory, automate stock level alerts, and ensure sensitive data (e.g., pricing, supplier contacts) is encrypted using AWS Key Management Service (KMS).


## Overview
This solution is designed to demonstrate real-world application of AWS serverless technologies in developing secure, production-grade backend systems. It is ideal for small-to-medium enterprises (SMEs), or as a technical demonstration for AWS Solution Architects and Cloud Developers.

## Features
KMS Encryption: Encrypt sensitive fields (e.g., prices, supplier info) in DynamoDB.

Serverless REST API: API Gateway + Lambda to manage inventory operations.

DynamoDB Storage: Fast, scalable NoSQL data layer.

SNS Alerts: Automatic low-stock notifications.

Athena/QuickSight Integration: Optional for inventory analytics and reporting.

## Project Architecture

![Project Architecture ](Project%20Architecture/IMS.JPG)



IAM Best Practices: Role-based access with least privilege.

## Architecture Components
Component	Service	Description
API Layer	API Gateway	RESTful endpoints for interacting with inventory data
Business Logic	AWS Lambda	Stateless compute functions for inventory CRUD operations
Data Store	DynamoDB	Secure, scalable NoSQL database
Data Encryption	AWS KMS	Field-level encryption for sensitive attributes
Notifications	SNS	Triggers alerts when stock falls below threshold
Optional Insights	Athena / QuickSight	Visualize and query inventory trends

## API Endpoints
Method	Endpoint	Description
POST	/item	Add new inventory item
GET	/item/{id}	Retrieve a single item
PUT	/item/{id}	Update item details or stock
DELETE	/item/{id}	Remove item from inventory
GET	/inventory	Get list of all items

## Security Highlights
AWS KMS used to generate and manage encryption keys.

Sensitive fields are encrypted at rest in DynamoDB using the aws-sdk within Lambda.

IAM roles tightly scoped to Lambda and specific DynamoDB table actions.

CloudWatch Logs enabled for Lambda for full observability.

## Folder Structure
.
├── lambda/
│   ├── createItem.js
│   ├── getItem.js
│   ├── updateItem.js
│   └── deleteItem.js
├── terraform/ or cloudformation/
│   └── ims-infra.tf / ims-infra.yaml
├── utils/
│   └── encryption.js
├── README.md
└── architecture/
    └── serverless KMS.JPG
    
## Setup & Deployment
Prerequisites:
AWS CLI configured

Node.js (for Lambda code)

Terraform or AWS CloudFormation (infrastructure as code)

KMS key pre-created

Using Terraform (example):
cd terraform
terraform init
terraform apply
Deploy Lambda Functions:
Use AWS Console or CLI to deploy zip packages for each Lambda.

## Future Enhancements
Cognito user authentication (admin vs staff roles)

Product image uploads via S3

Bulk import/export inventory from CSV

Version control for stock changes using DynamoDB Streams

## Author
Emma (Cloud Architect)
GitHub: Cloud-Architect-Emma
LinkedIn: www.linkedin.com/in/cloud-architect-emma

## License
MIT License
