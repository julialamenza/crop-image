# Infrastructure

## Architecture
We have a simple serverless architecture, with an api gateway, a lambda and they upload it to S3.


# Result
The code is deployed on my personal AWS account.

You can upload your image with this command:
```shell
curl -X POST <your endpoint> \
--form 'file=@filename.jpg' \
--form 's3Key=filename.jpg'
```


## Project information
### Prerequisite
Before deploying the project you should have `docker` and set up your AWS credentials.

# Infra as code
The infrastructure as code of this app is build with the [`serverless` framework](https://www.serverless.com/).
The configuration is available in the [serverless.yml](https://github.com/julialamenza/crop-image/blob/dev/serverless.yaml) file.

### Build the app
If you want to deploy your lambda to the dev environment, you can still use:
```shell
npm run deploy
```
We are using **docker** to build and deploy the lambda.
**Don't forgot to set your profile** on [package.json](https://github.com/julialamenza/crop-image/blob/dev/package.json) file to be able to create the stack correct

## Logging

Based on `serverless` :

`npm run infra:logs:cropimage`

All the logs of the lambda are available in cloudwatch.

## Monitoring

Based on `serverless` :

`npm run infra:metrics:cropimage`

When you need more capabilities, you can directly use AWS CloudWatch service (console or API)


# Tracing
Xray is activate on the API Gateway and the lambda.
You can also use the Xray SDK to add monitoring inside your lambda.

## Clean up

Based on `serverless` :

`serverless remove -v`
