My Summary
-------------------------------

Amazon API Gateway  
https://docs.aws.amazon.com/ko_kr/apigateway/latest/developerguide/integrating-api-with-aws-services-lambda.html

- IAM Setting  
```
AWSLambdaFullAccess  
AmazonAPIGateWay Adminstrate  
AmazonCognitoPwerUser  
```

정책변수를 통해서 접근아이피, 현재시간에 따른 접근, https 접근여부, 특정웹페이지 접근여부
를 설정할수있다.
```
Condition -> IpAddress
Condition -> NotIpAddress
aws:SourceIP

Condition -> DateGreaterThan -> DateLessThan
aws:CurrentTime

Condition -> Bool
aws:SecureTransport

aws:Referer
```

AWS 루트 계정 MFA(Multi-Factor Authentication) 설정 권장  
aws.amazon.com/iam/details/mfa  

1. 정책(Policy)
2. 권한(Authorization)
3. 인증(Authentication)
3-1. access key
3-2. secret access key
(AWS CLI와 SDK가 자동으로 작업함)

사용자는 그룹에 속할수있으며, 역할은 사용자,애플리케이션,서비스에 부여받을수있다.
사용자는 지속적인 자격증명을 가지며, 주기적으로 변경을 권장
역활은 임시자격증명(AWS STS(Security Token Service)이 부여된다.

계정 (배포 그룹, 테스트 그룹, DBA 그룹)

- AWS CLI  
```
aws Lambda list-functions  
aws lambda invoke help  

aws lambda invoke --function-name greetingsOnDemand --payload "{""name"":""JO""}" output.txt
aws lambda invoke --function-name greetingsOnDemand --payload "{}" output.txt
```

- Tip
Restful api 설계방법
https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm

Welcome to AWS Lambda in Action
-------------------------------

This source code distribution is a companion to the
*AWS Lambda in Action: Event-Driven Serverless Application* book available from Manning Publications.

There are a few live demos available at
  https://awslambdainaction.com/#livedemos

To purchase an electronic or printed copy of the book,
visit
  https://www.manning.com/books/aws-lambda-in-action

Requirements
------------

To create Lambda functions and execute the code,
you need an Amazon Web Services (AWS) account.

To create a new account, please see:
  https://aws.amazon.com/free/

Running
-------

To create functions, start from the AWS Lambda web console at:
  https://console.aws.amazon.com/lambda

For detailed information on how to use the source code,
please look at the relative chapters in the book.

    Chapter02/
      greetingsOnDemand.js                  Function to greet by "name" in Node.js
      greetingsOnDemand.py                  Function to greet by "name" in Python
      customGreetingsOnDemand.js            Function for a custom greet by "name" in Node.js
      customGreetingsOnDemand.py            Function for a custom greet by "name" in Python
    Chapter03/
      whatIsMyIp.js                         Function to echo the IP address in input in Node.js
      whatIsMyIp.py                         Function to echo the IP address in input in Python
    Chapter04/
      Policy_RW_S3.json                     Policy to give read/write access to an Amazon S3 bucket
      Policy_RW_console_S3.json             Adding permissions required by the Amazon S3 web console
      Policy_RW_prefix_console_S3.json      Limiting access to a prefix inside an Amazon S3 bucket
      Policy_RW_DynamoDB.json               Policy to give read/write access to a DynamoDB table
      Policy_RW_query_DynamoDB.json         Adding query permissions to Amazon DynamoDB
      Policy_Lambda_basic_exec_role.json    Lambda basic execution role permissions
      Policy_Lambda_trust.json              Lambda basic execution role trust relationships
    Chapter05/
      FaceDetection/                        Function using OpenCV to detect faces.
      Scheduled/                            Function to clean up your S3 bucket. Can be scheduled.
      SubscribeToS3/                        Function triggered by a new picture on Amazon S3.
    Chapter06/
      Policy_Cognito_private_S3.json        Policy to give access to private folders on Amazon S3
      Policy_Cognito_public_S3.json         Policy to give access to public folders on Amazon S3
      Policy_Cognito_private_DynamoDB.json  Policy to give private access to DynamoDB
      Policy_Cognito_shared_DynamoDB.json   Policy to give shared access to DynamoDB
      Policy_Cognito_trust_auth.json        Amazon Cognito trust policy for the unauthenticated role
      Policy_Cognito_trust_unauth.json      Amazon Cognito trust policy for the authenticated role
    Chapter07/
      GreetingsOnDemand/                    Calling a function via JavaScript from a static web page
      CustomGreetingsOnDemand/              Another example of calling a function via JavaScript
      SimpleWebsite/                        Dynamic web site using Amazon API Gateway and EJS templates
    Chapter09/
      SampleAuth/                           Sample serverless authentication service
    Chapter10/
      SampleAuth/                           Same as before (more features in this chapter)
    Chapter11/
      MediaSharing/                         Sample media sharing web app
    Chapter13/
      app.py                                Sample app using Chalice
      greetingsOnDemand.js                  Same old function, to test local development
      greetingsOnDemand.py                  Same old function, to test local development
      runLocal.js                           Sample wrapper to run JavaScript functions locally
      runLocal.py                           Sample wrapper to run Python functions locally
      lambdaTest.js                         Function to test other functions, based on the blueprint
    Chapter14/
      CloudFormation/                       CloudFormation templates to create Lambda functions
      greetingsOnDemand/                    Same old function, to play with AWS CloudFormation

Contact Information
-------------------

Manning provides an Author Online forum accessible from:
  https://forums.manning.com/forums/aws-lambda-in-action

For general AWS Lambda information and support, please visit
AWS's website for pointers to FAQ's, documentation and pricing.

The main AWS Lambda website is:
  https://aws.amazon.com/lambda
