# aws_three_tier_architecture_deployment
This is a porject for aws cloud beginner
project purpose
- CREATE HIGHLY AVAILABLE INFRA
- CREATE FAULT TOLERANT INFRA
- SCALABLE INFRA
- HIGHLY SECURE INFRA
  



## Step 1: Download Code from GitHub in Your Local System

## Step 2: Create Two S3 Buckets
- Create one S3 bucket for storing web-server & app-server code.
- Upload the code to your S3 from your local system.
- Create another S3 bucket for VPC flow logs.

## Step 3: Create IAM Role with Policies
- S3 read only.
- SSM managed instance core.

## Step 4: Create VPC, Subnets, IGW, NAT-GW, RT
- Enable auto-assign public IP for web-tier public subnets.
- Create flow logs for VPC & use the S3 bucket created above.

## Step 5: Create Security Groups
1. **External-Load-Balancer-SG** --> HTTP (80): 0.0.0.0/0.
2. **Web-Tier-SG** --> HTTP --> Ext-LB-SG.
3. **Internal-Load-Balancer-SG** --> HTTP --> Web-Tier-SG.
4. **App-Tier-SG** --> Port 4000 --> Internal-LB-SG.
5. **DB-Tier-SG** --> MySQL (3306) --> App-Tier-SG.

## Step 6: Create DB Subnet Group & RDS
- Create DB subnet group.
- Create RDS - Multi-AZ.
- Place them in DB subnet group created above.

## Step 7: Create Test App Server, Install Packages, Test Connections
- [Test App-Server Commands](https://github.com/anirudhsom123/aws_three_tier_architecture_deployment/blob/main/app-server-commands)
- Create AMI.
- Create launch template using AMI.
- Create target group.
- Create internal load balancer.
- Create autoscaling group.
- Edit `nginx.conf` file in local system by adding Internal-LB-DNS & upload the file in S3.

## Step 8: Create Test Web Server, Install Packages (Nginx, Node.js (React)), Test Connections
- [Test Web-Server Commands](https://github.com/anirudhsom123/aws_three_tier_architecture_deployment/blob/main/web-server-commands)
- Create AMI.
- Create launch template using AMI.
- Create target group.
- Create external load balancer.
- Create autoscaling group.



## Step 9: Add External-ALB-DNS Record in Route 53

## Step 10: Create CloudWatch Alarms Along with SNS

## Step 11: Create CloudTrail

## Step 12: Deleting the Entire Infrastructure
- Delete CloudFront.
- Delete CloudWatch alarms.
- Delete records from Route 53.
- Delete load balancers, target groups, ASG, launch templates.
- Delete security group.
- Delete NAT gateway (it will take 5 mins).
- Release elastic IP.
- Delete VPC.
- Delete RDS subnet group, RDS.

---
