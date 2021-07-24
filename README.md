# aws_canaries_prod

CloudFormation Template to create Cloudwatch Synthetic Canaries to monitor data on our publicly available application endpoints (See list below)

Checks can only run in PROD as endpoints must be publicly available
The user that runs the CF template needs rights to create IAM objects and CloudWatchSyntheticsFullAccess (See https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Synthetics_Canaries_Roles.html)

To create run
```
aws cloudformation create-stack --stack-name CReATE-Canary-PRD --template-body file://./canary.yml --tags Key=owner,Value=System-Administrator --capabilities "CAPABILITY_NAMED_IAM"
```

For a console user to see Canary results the following policies rights are needed AmazonS3ReadOnlyAccess and CloudWatchReadOnlyAccess. To view the source code used by canaries, you also need the AWSLambdaReadOnlyAccess.

Endpoints checked
https://gitlab.create.army.mil
https://sonarqube.create.army.mil
https://jira.create.army.mil
https://keycloak.create.army.mil