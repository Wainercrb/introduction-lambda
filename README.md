# Lambda introduction
All this information is based on: Udemy course: [https://www.udemy.com/course/aws-lambda-serverless]

## A & Q
- Why use lambda framework?: Allows to the developers by quickly, faster and remove the obstacles that one may have when creating a lambda function, this framework integration CI/CO integrations.

### Advantages of using serverless
- All using programming (not manual clicks in AWS console)
- Can be integrated with CI/CD frameworks
- CloudWatch Log groups
- We barely scratched the surface of this framework!

### AWS functions & the serverless Framework core concepts
- Function: Piece of code that make an action
- Events: Anything that triggers an AWS Lambda function to execute
 - An AWS API Gateway HTTP endpoints
 - An AWS S3 bucket upload
- Resources: AWS infrastructure components which your function use
 - An AWS DynamoDB table (saving a component...)
 - An AWS S3 bucket (for saving audio files...)
 - An AWS SNS (sending messages asynchronously...)
- Services:
Framework's unit organization (project file)
- aws-nodejs-project
- Where you define your functions, the events that trigger them and the resources your functions use
- A service can be described in YAML or JSON

## To know
#### AWS functions limits
- Default timeout 3s, limit range (1s, 15s)
- Memory limit range (128MB, 10,240MB)

#### VPC for lambda functions
- VPC are virtual private clouds
 - Many companies use VPC to privately deploy their applications
 - By default lambda functions are not launched in a VPC

#### Running lambda locally for testing
We can run your lambda functions locally using AWS toolkit for VS Code

- With AWS Toolkit we can:
 - Test code locally with step-through debugging in a lambda env
 - Deploy your applications to the AWS region of your choice
 - Invoke your lambda functions locally or remotely
 - Specify function configurations such as an event payload and environment variables

#### Amazon SES
Amazon SES is a cloud email service provider that can integrate into any application for bulk email sending. Whether you send transactional or marketing emails, you pay only for what you use

#### Amazon SNS
Amazon Simple Notification Service (Amazon SNS) is a managed service that provides message delivery from publishers to subscribers (also known as producers and consumers).

#### CloudFormation
It's a service that gives developers and businesses an easy way to create a collect
ion of related AWS and third-party resources, and provision manage them in an orderly and predictable fashion

#### AWS step functions
A service that allows developer build visual workflows for business process
- Orchestrate data flow in an automated environment, for example: check if username and email provided are valid, if so, then allow users to open a new account
- Base on state machines and tasks


##### Benefits
- Build and deploy FAST!
 - Use the Workflow Studio to simply drag-and-drop
 - Express complex business logic as low-code, event-driven workflows
 - Connect services (AWS), systems or people quickly
- Write less integration code
 - Ready to use resources and services available
- Reliable and Scalable 
 - Used for small projects as well large
 - Reliable - has built-in try/catch, retry and rollback capabilities for error handling

##### States
Aren't the same thing as Tasks, they are one of the State Types

- **Pass:** Pushes input and output
- **tasks:** Takes input and produces output
- **Choice:** Allows the user to use Branching Logic based on the input
- **Wait:** It adds delays to State Machine Execution
- **Success:** Has and expected finish-line: dead-end that stops execution successfully
- **Fail:** Has an expected dead-end -stops execution with a failure
- **Parallel:** Implements parallel branches in execution -- use can start multiple states at once
- **Mapping** (Dynamic): Runs a set of steps for every input item

## Requirements
- node: v14.19.1
- npm: v6.14.16
- serverless: npm i -g serverless
- aws account
- AWS Toolkit for VS Code
- AWS CLI
- Docker
- AWS Serverless Application Model CLI (SAM): Allow us to define, test and deploy serverless application, some SAM benefits are:
 - **Single-deployment configuration:** Deploy the whole stack as sinble entity
 - **Extension for AWS CloudFormation:** Reliable cloudFormation stack deployment!
 - **Buil-in best practices:** Use AWS SAM to define and deploy your infrastructure as config
 - **Local debugging and testing:** Locally build, test and debug serverless apps!
 - **Depp integration with development tools:** Integrates well with many others AWS tools and services 

## Important commands
- Create project with template:
```sh 
sls create --template google-python --path hello-world-google-python
```
- Setup your aws credentials:
```sh 
serverless config credentials --provider aws --key your-key --secret your-secret profile your-profile
```
- Deploy function(make sure you are in the lambda folder):
```sh
sls deploy function -f your-function-name
```
- Serverless invoke function:
```sh
sls invoke -f function-name
```
- Print serverless logs by function:
```sh
sls log -f function-name
```
- Remove functions, dependencies of the function, logs, IAM roles and everything else the serverless has created:
```sh 
sls remove
```
- Create AWS SAM application
```sh
sam init
```
and then, pick option 1 (AWS Quick Start Templates)\
and then, pick option 1 (Hello World Example)\
and then, select **YES**
- Build SAM project
```sh
sam build
```
- Invoke SAM function locally
```sh
sam local invoke
```
- Deploy the AWS SAM to AWS Cloud
```sh
sam deploy --guided
```
- Hosting SAM the API locally
```sh
sam local start-api
```
- Invoke you SAM Lambda function directly
```sh
sam local invoke "YOUR_FUNCTION_NAME" -e/event.json
```
- Delete the stack
```sh
aws cloudformation delete-stack --stack-name sam-app --region us_SOMETHING
```

