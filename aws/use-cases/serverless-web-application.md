# Serverless web application

## Introduction <a href="#0-toc-title" id="0-toc-title"></a>

nholuongut makes deploying serverless applications a breeze. A step by step tutorial on how to deploy a Lambda application is available.

Deployment is a three-step process.

1. Create a zip file
2. Create a S3 bucket
3. Create a lambda function

Following is a video version of this tutorial:

{% embed url="https://youtu.be/MW62CrzVO2E" %}

## Step 1: Create a zip file <a href="#1-toc-title" id="1-toc-title"></a>

Generate a Zip package of your Lambda code. The Lambda function code should be at the root of the package. If you are using virtual env, all dependencies should be packaged. Refer to the AWS documentation for detailed instructions on how to generate a package. We personally prefer using tools like zappa and serverless.

## Step 2: Create a S3 Bucket <a href="#2-toc-title" id="2-toc-title"></a>

Navigate to **DevOps > Storage > S3 > +Add** button above the table. Give a name for your bucket or leave it blank and a name will be auto generated. Then Click on AWS Console Button to get into AWS console for this S3 bucket and upload the zip file we just created.

![](https://nholuongut.com/wp-content/uploads/2021/11/createotheraws.png)

## Step 3: Create a lambda function <a href="#3-toc-title" id="3-toc-title"></a>

Navigate to **DevOps > Serverless > Lambda > +Add** button above the table. Give a name for the Lambda function and other values. This will create the lambda function. Click on AWS console to go to the AWS console for this function. Test the function. Refer to AWS Lambda functions for more info. You can also look at one of the following tutorials for S3 backend web application or look at AWS documentation.

![](https://nholuongut.com/wp-content/uploads/2021/11/lambdamenu.png)
