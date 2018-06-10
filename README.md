# serverless
This repository is used for hands-on cloud security training on serverless computing in AWS.

It is based on https://github.com/serverless/examples/tree/master/aws-python-simple-http-endpoint

Prerequisites:
* Laptop with Unix type operating system, e.g. Mac OS X
*	Node.js
*	AWS credentials installed with AWS CLI
*	AWS account with appropriate IAM rights
*	Install Serverless Framework
```
$ npm install -g serverless
```

Clone the repository:
```
$ git clone git@github.com/celidor/serverless
```

Edit the profile line on serverless.yml to match the profile name of your AWS credentials, or remove the line altogether to use the default AWS profile.

Deploy serverless application in dev, test and prod:
```
sls deploy
sls deploy --stage test
sls deploy --stage prod
```

Serverless commands to obtain information about the deployment
```
sls info
sls deploy list
sls logs --function currentTime
sls metrics
```

To destroy the application in dev, test and prod:

```
sls remove
sls remove --stage test
sls remove --stage prod
```
