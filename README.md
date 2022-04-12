George Wen
11/04/2022

1. aws cli to run the deployment:
    aws cloudformation create-stack \
      --stack-name aws-tech-test \
      --template-body file://cf-template.yaml \
      --region us-east-1 \
      --parameters  ParameterKey=BucketName,ParameterValue=aws-test-ggww \
      --capabilities CAPABILITY_IAM 
2. Config athena query result location, run aws cli command:
    aws athena update-work-group     --work-group primary  --configuration-updates '{"ResultConfigurationUpdates": {"OutputLocation": "s3://aws-test-ggww/"}}'
2. Grant lambda IAM role permission to call comprehend api (in cf template).
3. Update lambda function to call comprehend sement (in cf template)
4. add crawler to update the table partition for newly arrived files
