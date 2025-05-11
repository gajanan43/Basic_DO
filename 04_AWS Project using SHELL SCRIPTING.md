# Here's a simple Bash script using AWS CLI to **report the usage of AWS resources** in your project. This includes:

* EC2 instances
* S3 buckets
* Lambda functions
* RDS databases
* Cost estimation (if enabled)

---

### Prerequisites:

* AWS CLI installed and configured (`aws configure`)
* IAM user with permissions to access required services

---

### 🖥️ **Script: `aws-usage-report.sh`**

```bash
#!/bin/bash
set -e

echo "=== AWS Usage Report ==="
echo "Generated on: $(date)"
echo "Region: $(aws configure get region)"
echo "===================================="

# EC2 Instances
echo -e "\n[EC2 Instances]"
aws ec2 describe-instances \
  --query 'Reservations[*].Instances[*].[InstanceId,InstanceType,State.Name,LaunchTime]' \
  --output table

# S3 Buckets
echo -e "\n[S3 Buckets]"
aws s3 ls

# Lambda Functions
echo -e "\n[Lambda Functions]"
aws lambda list-functions --query 'Functions[*].[FunctionName,Runtime,LastModified]' --output table

# RDS Instances
echo -e "\n[RDS Instances]"
aws rds describe-db-instances \
  --query 'DBInstances[*].[DBInstanceIdentifier,DBInstanceClass,Engine,DBInstanceStatus]' \
  --output table

# AWS Cost (Last Month)
echo -e "\n[AWS Cost - Last Month]"
aws ce get-cost-and-usage \
  --time-period Start=$(date -d "-1 month" +%Y-%m-01),End=$(date +%Y-%m-01) \
  --granularity MONTHLY \
  --metrics "UnblendedCost" \
  --query 'ResultsByTime[*].Total.UnblendedCost.Amount' \
  --output text

echo -e "\n=== End of Report ==="
```

---

###  How to Run:

1. Save this as `aws-usage-report.sh`
2. Make executable: `chmod 777 aws-usage-report.sh`
3. Run: `./aws-usage-report.sh`



