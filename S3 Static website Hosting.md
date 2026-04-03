# AWS S3 Static Website Hosting with CloudFront

## Objective

To host a static website using Amazon S3 and deliver it securely and efficiently using Amazon CloudFront.

---

## Services Used

* Amazon S3
* Amazon CloudFront

---

## Architecture

User → CloudFront (CDN + HTTPS) → S3 (Static Storage)

---

## Environment Setup

* Region: ap-south-2 (Hyderabad)
* Storage: S3 bucket (static hosting enabled)
* CDN: CloudFront distribution

---

## Steps Performed

### 1. Create S3 Bucket

* Created a unique S3 bucket
* Disabled “Block all public access”
* Enabled static website hosting
* Set index document as `index.html`

---

### 2. Upload Website Files

* Created a simple HTML file (`index.html`)
* Uploaded to S3 bucket

---

### 3. Configure Bucket Policy

* Added policy to allow public read access:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::<your-bucket-name>/*"
    }
  ]
}
```

---

### 4. Verify S3 Website

* Accessed website using S3 endpoint
* Confirmed successful hosting over HTTP

---

### 5. Create CloudFront Distribution

* Configured origin using S3 website endpoint
* Enabled HTTPS (Redirect HTTP to HTTPS)
* Used default cache behavior

---

### 6. Configure Default Root Object

* Set default root object to `index.html`

---

### 7. Verify CloudFront Deployment

* Accessed website using CloudFront domain
* Confirmed:

  * HTTPS enabled
  * Website loading correctly

---

## Observations

* S3 static website endpoint supports only HTTP
* CloudFront enables HTTPS using SSL/TLS
* Content is cached at edge locations for faster delivery
* Initial deployment takes a few minutes

---

## Key Learnings

* S3 is suitable for static websites due to its serverless nature
* CloudFront reduces latency by serving content from edge locations
* Cache can delay updates unless invalidated
* Proper origin configuration is critical (website endpoint vs bucket endpoint)

---


## Outcome

Successfully built a scalable, cost-efficient, and secure static website architecture using S3 and CloudFront.

---

## Cleanup

* Disabled and deleted CloudFront distribution
* Deleted S3 bucket and objects

---

## Commands / Files Used

```html
<!DOCTYPE html>
<html>
<head>
    <title>Boby Cloud Project</title>
</head>
<body>
    <h1>Arceus Cloud Project</h1>
    <p>Hosted on S3</p>
</body>
</html>
```
