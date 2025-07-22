# AWS Emulation Lab
Development of an AWS Emulation Lab in form of an IaC CloudFormation template. That template is used to build up a lab in AWS, which will offer the testing of security mechanisms based on Adversary Emulation.

- [AWS Emulation Lab Full](./AWS%20Emulation%20Lab%20Full)  
  Contains configurations and resources for building the lab environment without a Windows 10 instance, due to licence issues.

- [AWS Emulation Lab Attacker Only](./AWS%20Emulation%20Lab%20Attacker)  
  Contains configurations and resources for building the lab environment, which encompasses Caldera C2 with a middleman attacker ubuntu host. This is used to transport instances to other environments and test extern systems security mechanisms.
  This environment will be set up in near future.

## Creation of following infrastructure
- Caldera (Ubuntu EC2)
- Attacker (Ubuntu EC2)
- DVWA (Windows EC2)
- Juice Shop (Ubuntu EC2)
- bWAPP (Windows EC2)
- Splunk (Ubuntu EC2)
- Active Directory (Windows EC2)

## Used AWS Services
- EC2
- CloudWatch Logs
- CloudTrail
- VPC Flow Logs
- Systems Manager
- GuardDuty
- Other Infrastructure Services (CloudFormation, S3, IAM, EventBridge, DynamoDB, Lambda, KMS)

## Collected Log Sources
- VPC Flow Logs
- CloudTrail
- EC2 CloudWatch Agent Logs
  - Windows (System, Security, PowerShell, Sysmon)
  - Linux (Auditd, Kernel)
  - Web (Access Logs)

## Active Agents on Instances
- **EC2 CloudWatch Logs Agent** (bWAPP, DVWA, Juice Shop, Active Directory)
- **System Manager Agent** (Attacker, bWAPP, DVWA, Juice Shop, Active Directory)  
  All logs are pushed to CloudWatch and are pulled by Splunk via Splunk Add-on for AWS from CloudWatch.  
  Systems are accessible via Systems Manager Fleet

## Adhere to following information in order to setup the AWS Lab and prevent external access

### CloudFormationInfrastructure:
- Upload this file to CloudFormation in AWS and fill in all necessary information needed.
- Confirm that custom IAM definitions will be created.
- Start the process of building up the infrastructure as code.

### CalderaSecurityGroup:
- Immediately after uploading CloudFormationInfrastructure file to CloudFormation, upload CalderSecurityGroup to CloudFormation.
- The goal of this IaC template is to remove the EC2 instance (Caldera) from the internet and make it only accessible to the user.
