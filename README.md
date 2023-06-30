# CloudFormation Basics

This repository contains a CloudFormation template that allows you to easily deploy an S3 bucket in AWS with the ability to select the encryption type. The CloudFormation stack will prompt you to input values such as the bucket name and encryption type, and it will create the necessary resources accordingly. Additionally, this repository includes a README file and a screenshot showcasing the successful deployment.
Prerequisites

Before you begin, ensure that you have the following prerequisites in place:

-    An AWS account with appropriate permissions to create CloudFormation stacks.
-    AWS Command Line Interface (CLI) installed and configured on your local machine.

Usage

To deploy the CloudFormation stack and create the S3 bucket, follow these steps:

   - Clone this repository to your local machine or download the ZIP file and extract it.

  -  Navigate to the repository's root directory.

   - Open the s3-bucket.yaml file and review the template.

  - Modify the template as needed. You can change parameters such as the bucket name and encryption type.

   - Open a terminal or command prompt and navigate to the repository's root directory.

   - Run the following command to create the CloudFormation stack:

    bash
```
aws cloudformation create-stack --stack-name MyS3Bucket --template-body file://s3-bucket.yaml --parameters ParameterKey=BucketName,ParameterValue=my-bucket-name ParameterKey=EncryptionType,ParameterValue=SSE-S3
```
Replace my-bucket-name with your desired bucket name and SSE-S3 with your preferred encryption type. You can also use KMS as the encryption type.

Wait for the stack creation to complete. You can check the status of the stack creation by running the following command:

bash
```
aws cloudformation describe-stacks --stack-name MyS3Bucket --query "Stacks[0].StackStatus"
```
The stack creation is complete when the command returns CREATE_COMPLETE.

Once the stack creation is complete, you can access the CloudFormation outputs to retrieve important information about the created resources. Run the following command to get the outputs:

bash
```
    aws cloudformation describe-stacks --stack-name MyS3Bucket --query "Stacks[0].Outputs"
```
    The command will display the output values, including the S3 bucket URL and other relevant information.

Outputs can also be gotten from the AWS cloud console

Output Screenshot


![CloudFormation Stack Output](https://github.com/husseinalamutu/cloudformation/assets/94724734/d990f70b-8234-4480-97f1-708ba27f458e)



Screenshot
Below is a screenshot of a successful deployment of the CloudFormation stack:

![CloudFormation Stack Created Successfully](https://github.com/husseinalamutu/cloudformation/assets/94724734/0f6eba8f-a4b8-4f63-8f93-869faa1990c7)

Cleanup

To delete the CloudFormation stack and remove the S3 bucket, run the following command:

bash
```
aws cloudformation delete-stack --stack-name MyS3Bucket
```
Wait for the stack deletion to complete, which can be checked by running the describe-stacks command as shown earlier. The stack deletion is complete when the command returns DELETE_COMPLETE.

Please note that deleting the stack will also remove any objects stored in the S3 bucket, so make sure to back up any important data before initiating the deletion.
License

This project is licensed under the MIT License. Feel free to use, modify, and distribute the code as per the terms of this license.
