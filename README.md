# 🌩️ AWS Static Website Hosting with S3, CloudFront, Route 53, ACM, and CloudWatch

This project demonstrates how to host a secure static website using various AWS services under the **Free Tier**.  
It includes **SSL/TLS encryption**, **domain management**, **CDN caching**, and **monitoring** with CloudWatch.

---

## 🏗️ Architecture Overview

![Architecture Diagram](architecture-diagram.gif)

---

## ☁️ AWS Services Used

- **Amazon S3** – Hosts static website files (`index.html`, `error.html`)  
- **Amazon CloudFront** – CDN (Content Delivery Network) for global content delivery and HTTPS encryption  
- **AWS Certificate Manager (ACM)** – Provides free SSL/TLS certificates for secure HTTPS  
- **Amazon Route 53** – Manages the custom domain and DNS records  
- **Amazon CloudWatch** – Logs and monitors CloudFront activity for analytics and performance insights  

---

## 🌐 Example Website URL

**https://cloudwithpaula.click**  
*(This website was hosted temporarily for demonstration purposes using AWS Free Tier resources.)*

---

## ⚙️ Step-by-Step Setup Summary

### 1️⃣ Create an S3 Bucket
- Name the bucket after your domain name (e.g., `cloudwithpaula.click`)  
- Enable *Static Website Hosting*  
- Upload `index.html` and `error.html`  
- Make the bucket publicly accessible  

### 2️⃣ Request a Certificate (ACM)
- Go to **AWS Certificate Manager**  
- Request a certificate in **us-east-1 (N. Virginia)** for your domain and `www` subdomain  
- Validate using **DNS via Route 53**  
- Wait for the certificate to be **Issued**

### 3️⃣ Create a CloudFront Distribution
- **Origin domain:** your S3 *website endpoint*  
- Attach your **ACM certificate** (from us-east-1)  
- Add both domain names: `cloudwithpaula.click` 
- Redirect **HTTP → HTTPS**

### 4️⃣ Configure Route 53
- Create an **A record (alias)** pointing your domain to the CloudFront distribution  

### 5️⃣ Enable CloudWatch Logging
- Go to **CloudFront → General → Logging and monitoring**  
- Create an **Access Log Delivery** to an S3 bucket  
- View logs in **CloudWatch Logs**

---

## 💰 Teardown & Cost Management

To stay within the **AWS Free Tier**, it’s best to disable or delete resources after testing:

- Delete the **CloudFront distribution**  
- Delete the **S3 bucket** (after downloading your files)  
- Delete your **Route 53 hosted zone** (if not needed)  
- Remove the **ACM certificate** if no longer used  
- Disable **CloudWatch logs** to avoid storage costs  

> 🧹 *These configurations are reversible for future redeployment.*

---

## 🎯 Learning Outcomes

- Deployed a static website using AWS global infrastructure  
- Configured HTTPS using **ACM** and **CloudFront**  
- Managed DNS routing with **Route 53**  
- Implemented **CloudWatch logging** for observability  
- Practiced **cost-efficient cloud resource management**

---

## 🗂️ Repository Structure

```plaintext
aws-static-website-deployment/
│
├── README.md                ← this documentation  
├── architecture-diagram.gif ← architecture image  
├── index.html               ← static site file  
└── cloudfront-logs-example/ ← sample CloudFront access log
```
---
### 📊 CloudFront Logs
CloudFront logging was enabled and configured to store logs in an S3 bucket.  
A sample log file (`sample-log.json`) is included in the `cloudfront-logs-sample/` folder to demonstrate successful logging and monitoring.

---
### 🪶 Author
**Cloud with Paula**  
Cloud & AI Enthusiast  
