# Task: Configure CloudFront to Cache Load Balancer URL

## Objective
Students will configure Amazon CloudFront as a content delivery network (CDN) to cache content from a load balancer URL, improving performance and reducing latency for end users.

## Prerequisites
- AWS account with appropriate permissions
- Existing Application Load Balancer (ALB) with a valid DNS name
- Understanding of CloudFront and caching concepts

## Tasks

### 1. Create a CloudFront Distribution
- Navigate to the CloudFront service in the AWS Management Console
- Click "Create distribution"
- Select "Web" as the distribution type
- Configure the origin with your load balancer URL (e.g., `my-alb-123456.us-east-1.elb.amazonaws.com`)

### 2. Configure Origin Settings
- Set the protocol policy to "HTTPS only" or "Match Viewer"
- Enable "HTTP/2" and "HTTP/3 (QUIC)"
- Add HTTP header forwarding if needed for dynamic content

### 3. Set Cache Behaviors
- Configure cache TTL (Time To Live):
  - Default TTL: 86400 seconds (24 hours)
  - Minimum TTL: 0 seconds
  - Maximum TTL: 31536000 seconds (365 days)
- Select "Compress objects automatically" for text-based content
- Choose appropriate cache policies for your use case

### 4. Enable Security
- Enforce HTTPS viewers
- **Disable** AWS WAF rules
- Configure custom SSL certificate (optional)

### 5. Verify and Deploy
- Review the distribution settings
- Click "Create distribution"
- Wait for the distribution status to change from "In Progress" to "Enabled"
- Note the CloudFront domain name (e.g., `d111111abcdef8.cloudfront.net`)

### 6. Test the Distribution
- Access your content through the CloudFront domain name
- Verify that requests are being served from edge locations
- Check CloudFront metrics in the console to confirm cache hits

## Success Criteria
- [ ] CloudFront distribution is created and deployed
- [ ] Load balancer URL is configured as the origin
- [ ] Distribution status shows "Enabled"
- [ ] Content is accessible via CloudFront domain name
- [ ] Cache metrics show successful hits