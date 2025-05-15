# Day-13

# AWS Services for DevOps:

### 1. EC2 (Elastic Compute Cloud):

**What is EC2?**
EC2 is a service by AWS that provides **virtual machines** (called instances) in the cloud.

### 🔧 **Key Points:**

* **Virtual Server:** EC2 allows you to rent virtual computers (like a desktop/laptop in the cloud).
* **Scalable:** You can launch 1 or 1000 instances easily depending on your needs.
* **Customizable:** You can choose:

  * Operating system (Linux, Windows, etc.)
  * CPU, RAM, storage
  * Network configuration
* **Pay-as-you-go:** You pay only for the time you use (hourly or per second).
* **Secure:** You can control access using **security groups** and **key pairs**.
* **Elastic:** Easily scale up/down based on traffic or demand.


### 📦 **Example Use Cases:**

* Hosting websites or web apps
* Running backend servers
* Machine learning training jobs
* Development and testing environments


### Real-World Example:

You want to host a Node.js application?
➡️ You launch an **EC2 instance**, install Node.js, upload your code, and run the server.

Great! Here's a simple and clear explanation of all the listed AWS services:

---

## 2. VPC (Virtual Private Cloud):

**VPC** lets you create your **own private network** inside AWS.

* Like setting up a private data center.
* You control IP range, subnets, routing, and firewall rules.
* Helps secure your resources (e.g., EC2, RDS) in isolated networks.


## 3. EBS (Elastic Block Store):

**EBS** provides **hard drive storage** for EC2 instances.

* It’s like a virtual USB drive attached to your EC2.
* Can be detached/attached to any instance.
* Stores OS, data, databases, etc.
* Types: gp3, io2, sc1 (for performance/cost options).

## 4. S3 (Simple Storage Service):

**S3** is used to store **any kind of data** (files, images, videos, backups, etc.).

* Object storage service.
* Unlimited storage.
* Accessible from anywhere over the internet.
* Used for static website hosting, backup, logs, etc.

## 5. IAM (Identity and Access Management):

**IAM** controls **who can access what** in your AWS account.

* Manage users, groups, roles, and permissions.
* Enforces security with policies.
* Example: Give developer read-only access to S3.


## 6. CloudWatch:

**CloudWatch** monitors your **AWS resources and applications**.

* Collects metrics (CPU, memory, disk usage).
* Sends alerts when something goes wrong.
* Used for logs, dashboards, and alarms.

## 7. Lambda:

**Lambda** lets you **run code without servers**.

* Just upload your code; AWS handles servers.
* Supports Node.js, Python, Java, etc.
* Good for event-based tasks (e.g., S3 file upload triggers a function).


## 8. Cloud Build Service (Not AWS, it's a **Google Cloud** service):

For AWS, the equivalent is **AWS CodeBuild**.

* Automates **build and testing** of code.
* Used in CI/CD pipelines.
* Pulls code, runs tests, and builds deployable apps.

## 9. AWS Config:

Tracks **resource changes** and **compliance** in your AWS account.

* Keeps a history of configuration changes (e.g., who changed a security group).
* Helps with audits and security analysis.


## 10. Billing and Costing:

AWS provides detailed **billing and usage reports**.

* Check charges per service.
* Set **budgets and alerts**.
* Use **Cost Explorer** to visualize spending.

---

## 11. AWS KMS (Key Management Service):

**KMS** helps you manage **encryption keys** for your data.

* Secure your data in S3, EBS, RDS using keys.
* AWS manages or you can create your own keys.
* Integrated with other AWS services.

---

## 12. CloudTrail:

**CloudTrail** tracks **all API calls** made in your AWS account.

* Who did what, when, and from where.
* Useful for security audits and investigations.


## 13. EKS (Elastic Kubernetes Service):

**EKS** runs **Kubernetes clusters** on AWS.

* Fully managed by AWS.
* You focus on deploying containers; AWS manages the control plane.
* Works with standard Kubernetes tools.


## 14. Fargate & ECS:

**ECS (Elastic Container Service):**

* Run **containers** (like Docker) without managing servers.
* Two launch types:

  * **EC2** (you manage server)
  * **Fargate** (serverless)

**Fargate:**

* You run containers **without provisioning servers**.
* AWS handles infrastructure.


## 15. ELK (Elasticsearch, Logstash, Kibana):

**ELK Stack** is used for **log management and analysis**.

* **Elasticsearch:** Search and analyze logs.
* **Logstash:** Collects and processes logs.
* **Kibana:** Visualizes logs in graphs and dashboards.
* AWS version: **Amazon OpenSearch Service** (formerly Elasticsearch Service).


