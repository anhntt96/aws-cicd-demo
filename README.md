# aws-cicd-demo

Before you create your taskdef.json file, you need to set some environment variables. To create the variables, enter the following command:

```
AWS_REGION=$(curl -s http://169.254.169.254/latest/dynamic/instance-identity/document | jq -r .region) 
FAMILY=$(aws ecs list-task-definition-families --status ACTIVE --output text | awk '{print $NF}') 
ACCOUNT_ID=$(aws sts get-caller-identity --query Account --output text) 
printf "You are using $AWS_REGION region\nYour task definition family is $FAMILY\nYour account ID is $ACCOUNT_ID\n"
```