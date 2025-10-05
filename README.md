AWS Static Website Hosting with S3, CloudFront, Route 53, ACM, and CloudWatch
---
This project demonstrates how to host a secure static website using various AWS services under the Free Tier.  
It includes SSL/TLS encryption, domain management, CDN caching, and  monitoring.

Architecture Overview

---
AWS Services Used
- Amazon S3 – Hosts static website files (`index.html`, `error.html`)
- Amazon CloudFront – CDN for global content delivery and HTTPS encryption
- AWS Certificate Manager (ACM) – Provides free SSL/TLS certificates for secure HTTPS
- Amazon Route 53 – Manages the custom domain and DNS records
- Amazon CloudWatch – Logs and monitors CloudFront activity for analytics and performance insight

 Example Website URL
https://cloudwithpaula.click 
(This website was hosted temporarily for demonstration purposes using AWS Free Tier resources.)

Step-by-Step Setup Summary
1. Create an S3 Bucket
- Name the bucket after your domain name (e.g., `cloudwithpaula.click`)
- Enable Static website hosting
- Upload `index.html` and `error.html`
- Make the bucket publicly accessible

2. Request a Certificate (ACM)
- Go to AWS Certificate Manager
- Request a certificate in **us-east-1 (N. Virginia)** for your domain and `www` subdomain
- Validate using DNS via Route 53
- Wait for the certificate to be Issued

3. Create a CloudFront Distribution
- Origin domain: select your S3 website endpoint
- Attach your ACM certificate (from us-east-1)
- Add both domain names: `cloudwithpaula.click` and `www.cloudwithpaula.click`
- Redirect HTTP → HTTPS

4. Configure Route 53
- Create an A record (alias) pointing your domain to the CloudFront distribution
- Optionally add a CNAME record for `www`

5. Enable CloudWatch Logging
- Go to CloudFront → General → Logging and monitoring**
- Create an Access log delivery to an S3 bucket
- View logs in CloudWatch Logs

 Teardown & Cost Management

To stay within the AWS Free Tier, it’s best to disable or delete resources after testing:
- Delete the CloudFront distribution
- Delete the S3 bucket (after downloading your files)
- Delete your Route 53 hosted zone (if not needed)
- Remove the ACM certificate if no longer used
- Disable CloudWatch logs to avoid storage costs

*(All actions can be reversed if you wish to redeploy later.)*

Learning Outcomes

- Deployed a static website using AWS global infrastructure  
- Configured HTTPS using AWS Certificate Manager and CloudFront  
- Managed DNS routing with Route 53  
- Implemented CloudWatch logging for observability  
- Practiced cost-efficient cloud resource management  
---
 Repository Structure
aws-static-website-deployment/
│
├── README.md ← this documentation
├── architecture-diagram.png ← architecture image
├── index.html ← static site file
└── cloudfront-logs-example/ ← optional sample logs or screenshots

---
Key Takeaway
This project illustrates how AWS services integrate to create a secure, scalable, and globally available static website 
---
🪶 Author
Paula K
Cloud & AI Enthusiast


