# AWS Emulation Lab
Development of an AWS Emulation Lab in form of an IaC CloudFormation template. That template is used to build up a lab in AWS, which will offer the testing of security mechanisms based on Adversary Emulation.

- [AWS Emulation Lab No Win10](./AWS Emulation Lab No Win10)  
  Contains configurations and resources for building the lab environment without a Windows 10 instance, due to licence issues. 
  Includes:

- [AWS Emulation Lab Win10](./AWS Emulation Lab Win10)  
  Contains configurations and resources for building the lab environment with a Windows 10 instance.


## Creation of following infrastructure:
- EC2 Caldera Server
- EC2 DVWA Server
- EC2 Juice Shop Server
- EC2 Active Directory
- (EC2 Windows 10)

## Used AWS Services after Lab Setup:
- CloudFormation
- EC2
- CloudWatch
- CloudTrail
- Systems Manager
- GuardDuty
- SecurityHub
- DynamoDB
- S3 Bucket

## Collected Log Sources:
- VPC Flow Logs
- CloudTrail
- EC2 CloudWatch Agent Logs (System , Security , PowerShell , Sysmon , Web)

## Adhere to following information in order to setup the AWS Lab and prevent external access.

### CloudFormationInfrastructure:
- Upload this file to CloudFormation in AWS and fill in all necessary information needed.
- Confirm that custom IAM definitions will be created.
- Start the process of building up the infrastructure as code.

### CalderaSecurityGroup:
- Immediately after uploading CloudFormationInfrastructure file to CloudFormation, upload CalderSecurityGroup to CloudFormation.
- The goal of this IaC template is to remove the EC2 instance (Caldera) from the internet. 
