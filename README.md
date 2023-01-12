# Lambda introduction

## A&Q
- Why use lambda framework?: Allows to the developers by quickly, faster and remove the obstacles that one may have when creating a lambda function, this framework integration CI/CO integrations

## Requirements
- node: v14.19.1
- npm: v6.14.16
- serverless: npm i -g serverless
- aws account

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
