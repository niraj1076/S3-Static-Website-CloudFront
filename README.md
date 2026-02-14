# S3 Static Website Hosting with CloudFront

## Project Overview

This project demonstrates hosting a multi-page static website on AWS using Amazon S3 and improving performance using Amazon CloudFront.

The website template was downloaded for learning purposes. The focus of this project was cloud deployment, CDN integration, and understanding scalable static hosting architecture.

---

## Architecture

User → CloudFront (CDN) → Amazon S3 (Static Website Hosting)

---

## AWS Services Used

- Amazon S3 – Static website hosting  
- Amazon CloudFront – Content Delivery Network (CDN)  
- IAM – Access control and permissions  

---

## Project Structure

```
S3-Static-Website-CloudFront/
│
├── website/        ← all HTML files inside this folder
│    ├── index.html
│    ├── css/
│    ├── js/
│    └── ...
│
└── README.md

```
---

## Implementation Steps

### Step 1: Prepare Static Website Files
- Downloaded a multi-page HTML template.
- Verified all folders: css, js, images, plugins, upload.

### Step 2: Create S3 Bucket

1. Go to AWS Console → S3  
2. Create a new bucket  
3. Disable "Block all public access"  
4. Enable Static Website Hosting  
5. Configure:
   - Index document → `index.html`
   - Error document → `404error.html`

### Step 3: Upload Website Files

- Uploaded all HTML files  
- Uploaded css/, js/, images/, plugins/, upload/ folders  
- Verified correct folder structure inside S3  

### Step 4: Configure Bucket Policy

Added public read access to allow website access:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadAccess",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}
```

### Step 5: Create CloudFront Distribution

1. Go to CloudFront  
2. Create Distribution  
3. Set Origin → S3 bucket  
4. Set Default Root Object → `index.html`  
5. Viewer Protocol Policy → Allow HTTP  
6. Create Distribution  

Wait for deployment (approximately 5–10 minutes).

### Step 6: Access Website via CloudFront

- Copied CloudFront domain name  
- Verified multi-page navigation  
- Confirmed static assets (CSS, JS, images) load correctly  

---

## Key Learnings

- Difference between S3 REST endpoint and Website endpoint  
- Static website hosting configuration  
- Writing S3 bucket policies  
- CloudFront CDN integration  
- Multi-page static deployment architecture  

---

## Architecture Benefits

- Global content delivery via CDN  
- Reduced latency  
- Highly scalable  
- No server management required  
- Cost-effective hosting solution  

---

## Future Improvements

- Enable HTTPS using ACM  
- Add custom domain with Route53  
- Restrict direct S3 access using Origin Access Control (OAC)  
- Enable logging and monitoring  
- Automate infrastructure using Terraform  
- Add CI/CD using GitHub Actions  

---

## Author

Niraj Shrivastav  
Cloud & DevOps Engineer (Aspirant)
