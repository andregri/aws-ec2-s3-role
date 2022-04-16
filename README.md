# IAM Role attached to EC2 instance

`s3.yaml` creates an empty **bucket**.

`ec2.yaml` creates the following resources:
- a **role** for ec2 with a permission policy to list bucket objects
- an **instance profile** related to the previous role
- a **security group** that allows ingress SSH traffic
- a **EC2 instance** with the previous security group and instance profile

To verify that the EC2 assumed the role, SSH into the instance and run:
```
curl http://169.254.169.254/latest/meta-data/iam/info
```

To verify that the EC2 instance can list the bucket objects run:
```
aws s3 ls training-bucket-andrea
```
