## Introduction
This project is a demonstration on how to use **AWS SAM local** to simulate a
local **AWS API Gateway** pointing to a local **lambda function** (using **Go** as runtime)
for local development.

## Links
- [aws-sam-cli](https://github.com/awslabs/aws-sam-cli)
- [AWS Serverless Application Model (SAM) doc](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html)
- [Original Reference Project](https://github.com/harryleesan/local-lambda-go)
## Usage

Pre - Requirement: set GOPATH in enviroment variable. I used D:\go
Download the zip tool first:
```bash
go get -u github.com/aws/aws-lambda-go/cmd/build-lambda-zip
```

1. Compile the `main.go` into a binary

  ```bash
  Cmd> set GOOS=linux
  go build -o main main.go
  ```
2. ## Local dev Env:
  - AWS Command Line Interface [(AWS CLI Install)](https://docs.aws.amazon.com/cli/latest/userguide/install-windows.html#install-msi-on-windows) and Docker for Windows [install](https://docs.docker.com/docker-for-windows/install/)
  - cmd > aws configure
  configure AWS Access Key ID,  AWS Secret Access Key, Default region name and Default output format ( Find your Access Key ID,  AWS Secret Access Key on  https://console.aws.amazon.com/iam/home?region=ap-south-1#/security_credentials  > Aceess Keys > Create New Access Key).

  - docker pull lambci/lambda

3. Install [SAM Local](https://github.com/awslabs/aws-sam-local)

4. Start the **SAM Local** server

  ```bash
  sam local start-api
  ```

5. Access the API via Postman

![sam-api](https://github.com/harryleesan/local-lambda-go/blob/master/screenshot/Sam-output.png)

 Post data print as the response.

6. Generate Build and upload lambda into AWS
```bash
D:\go\bin\build-lambda-zip.exe -o main.zip main
```
upload main.zip when create a lambda function in AWS



