[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-f4981d0f882b2a3f0472912d15f9806d57e124e0fc890972558857b51b24a6f9.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=9729232)
# G1T5 Project
The main repository for CS301-g1-team5 project submission includes multiple folders for the individual components that are deployed on AWS to make the transaction processing service happen and CloudFormation template designed for setting up basic AWS networking infrastructure. There are also sample sql population statements for the initial insertion of data and a spend_demo to showcase sample transaction processing functionalities.

## Team Members
Austen\
Hidir\
Chen Kun\
Jun Hua\
Tan Zheng\
Edwin\
Khai Soon\

## CloudFormation Template

The CloudFormation Template component sets up the necessary networking infrastructure for the application. This includes creating the VPC (Virtual Private Cloud), subnets, and security groups.

To set up the CloudFormation Template, run the following command:
`aws cloudformation create-stack --stack-name <stack-name> --template-body file://<path/to/template.yml> --parameters file://<path/to/parameters.json>`

To delete the CloudFormation stack, use the following command:
`aws cloudformation delete-stack --stack-name <stack-name>`

## G1T5 Backend

The G1T5 Backend component is built using Java and Spring Boot. It provides the transaction processing service for the application.
This image will be built and pushed to ECR and the service will be deployed on ECS fargate.

To install the necessary dependencies, run the following command:

`mvn install`

To build the Docker image, use the following command:

`docker build -t g1t5-backend .`

Finally, to run the Docker container, use the following command:

`docker run -p 8080:8080 g1t5-backend`

## G1T5 Batch
The G1T5 Batch component is built using .NET Core. It provides the batch processing functionality for the application. This service is to ingest the CSV from the SFTP Server and push into AWS SQS.

To run the component, use the following command:
`dotnet run`

Alternatively you can build the Docker image, use the following command:
`docker build g1t5-batch .`

## G1T5 Frontend
The G1T5 Frontend component is built using Node.js and React. It provides the user interface for the application. This service is deployed on AWS Amplify and configured with AWS Cognito to provide authentication service.

To install the necessary dependencies, run the following command:
`npm install`

To start the frontend, use the following command:
`npm run start`

## G1T5 LambdaCRUD
The G1T5 LambdaCRUD component is built using the Serverless Framework and AWS Lambda. It provides the serverless API for the application. This service will be deployed on AWS Lambda for REST APIs invokation from the API Gateway.

To install the necessary dependencies, run the following command:
`npm install`

To run the component locally, use the following command:
`sls offline`

To deploy the component, use the following command:
`sls deploy`
