# Hosting a Static Website on Amazon S3

![Project Cover](https://github.com/EvelioMorales/Static-Website-hosting/blob/main/assets/01_project_cover_screenshot.png)

## Project Overview

This project demonstrates how to host a static website using Amazon S3.

Amazon S3, also known as Amazon Simple Storage Service, is an object storage service used to store and retrieve files such as HTML pages, images, CSS files, JavaScript files, documents, and other static assets.

In this project, I used Amazon S3 to upload website files, enable static website hosting, configure public access, troubleshoot a `403 Forbidden` error, and successfully access the website through the S3 website endpoint.

---

## Real-World Scenario

A company or developer may need a simple, low-cost way to host a static website without managing servers.

Amazon S3 can be used to host static websites such as:

- Portfolio websites
- Landing pages
- Documentation sites
- Resume websites
- Basic business websites
- Project demo pages

This project simulates deploying a static website using AWS storage infrastructure.

---

## Technologies Used

- Amazon Web Services
- Amazon S3
- S3 Bucket
- Static Website Hosting
- HTML
- Website Assets
- Access Control Lists
- S3 Bucket Endpoint
- AWS Management Console

---

## Skills Demonstrated

- Creating an Amazon S3 bucket
- Uploading static website files
- Enabling static website hosting
- Configuring an index document
- Understanding S3 bucket endpoints
- Troubleshooting S3 access errors
- Managing public access permissions
- Understanding basic AWS storage concepts
- Documenting a cloud project for GitHub

---

## What Is Amazon S3?

Amazon S3 is an object storage service that provides scalability, data availability, security, and performance.

In this project, I used S3 to store the files required for a static website.

The website files included:

- `index.html`
- Image and asset folders used by the website

The `index.html` file acts as the main page of the website. It tells the browser how the page should be structured and displayed.

---

## Architecture Summary

The website is hosted using a public S3 static website endpoint.

```text
User Browser
     |
     | HTTP Request
     |
S3 Static Website Endpoint
     |
     | Serves Website Files
     |
Amazon S3 Bucket
     |
     | Contains
     |
index.html + Website Assets
```

---

## Project Steps

## 1. Create an S3 Bucket

The first step was to create an S3 bucket in AWS.

An S3 bucket is a storage container used to hold website files and folders.

When creating the bucket, I selected a region close to the expected users to help reduce latency and improve website performance.

### Important Note About Bucket Names

S3 bucket names must be globally unique.

This means no other AWS account in any AWS region can have the same bucket name while that bucket exists.

![S3 Bucket Setup](https://github.com/EvelioMorales/Static-Website-hosting/blob/main/assets/06_s3_bucket_setup_screenshot.png)

---

## 2. Upload Website Files to S3

After creating the bucket, I uploaded the website files.

The uploaded files included:

```text
index.html
website asset folder
```

The `index.html` file is required because it is the default homepage that loads when users visit the website.

The asset folder contains supporting website files such as images, styling, and other resources needed for the page to display correctly.

![Upload Website Files to S3](https://github.com/EvelioMorales/Static-Website-hosting/blob/main/assets/02_upload_files_screenshot.png)

---

## 3. Enable Static Website Hosting

Next, I enabled static website hosting for the S3 bucket.

Steps:

1. Open the S3 bucket.
2. Go to the **Properties** tab.
3. Scroll to **Static website hosting**.
4. Click **Edit**.
5. Select **Enable**.
6. Enter the index document:

```text
index.html
```

7. Save the changes.

Static website hosting allows the S3 bucket to serve website content through a public website endpoint.

---

## 4. Access the S3 Website Endpoint

After static website hosting was enabled, Amazon S3 generated a bucket website endpoint URL.

The endpoint URL is used to access the website from a browser.

Example format:

```text
http://bucket-name.s3-website-region.amazonaws.com
```

This URL allows users to view the static website hosted from the S3 bucket.

![S3 Bucket Endpoint]([assets/03-bucket-endpoint.png](https://github.com/EvelioMorales/Static-Website-hosting/blob/main/assets/03_bucket_endpoint_screenshot.png))

---

## 5. Troubleshooting: 403 Forbidden Error

When I first visited the S3 bucket website endpoint, I received a:

```text
403 Forbidden
Access Denied
```

This happened because the S3 bucket content was still private.

By default, Amazon S3 does not automatically make uploaded files public. This is a security feature that helps protect files from unauthorized access.

![403 Forbidden Error]([assets/04-error-403.png](https://github.com/EvelioMorales/Static-Website-hosting/blob/main/assets/04_403_forbidden_screenshot.png))

---

## 6. Resolve the Access Denied Error

To resolve the error, I updated the permissions so the website files could be publicly accessed.

The issue was resolved by making the required website files and asset folder public.

After updating permissions, the website loaded successfully.

---

## 7. Second Issue: Asset Folder Name

After fixing the public access issue, I still experienced another problem because the uploaded asset folder had a different name than what the `index.html` file expected.

To fix this:

1. I deleted the incorrectly named folder.
2. I renamed the folder correctly.
3. I uploaded the folder again.
4. I made the folder public.
5. I tested the website endpoint again.

After correcting the folder name, the website displayed successfully.

![Website Hosted Successfully]([assets/05-success-website.png](https://github.com/EvelioMorales/Static-Website-hosting/blob/main/assets/05_success_website_screenshot.png))

---

## Final Result

The static website was successfully hosted on Amazon S3.

The final result confirmed that:

- The S3 bucket was created successfully.
- Website files were uploaded.
- Static website hosting was enabled.
- The website endpoint was generated.
- Access permission issues were resolved.
- The website loaded successfully in the browser.

---

## Validation

The project was validated using the following checks:

| Test | Expected Result | Actual Result |
|---|---|---|
| Create S3 bucket | Bucket is created successfully | Successful |
| Upload `index.html` | File appears in S3 bucket | Successful |
| Upload asset folder | Folder appears in S3 bucket | Successful |
| Enable static website hosting | Website endpoint is generated | Successful |
| Visit website endpoint | Website loads in browser | Initially failed with 403 |
| Fix permissions | Public files are accessible | Successful |
| Fix asset folder name | Website displays correctly | Successful |

---

## Error Encountered

### Error

```text
403 Forbidden
Access Denied
```

### Cause

The website files inside the S3 bucket were private.

### Resolution

The required website files and asset folder were made public so they could be accessed through the S3 website endpoint.

---

## Lessons Learned

Through this project, I learned how to:

- Create an Amazon S3 bucket
- Upload static website files
- Enable static website hosting
- Use an S3 website endpoint
- Troubleshoot a `403 Forbidden` error
- Understand the importance of correct file and folder names
- Manage public access for website content
- Use AWS S3 as a basic static website hosting service

This project helped me understand how cloud storage can be used to host simple web applications without needing a traditional web server.

---

## Security Considerations

Making S3 objects public should be done carefully.

For a basic static website, public access may be required so users can view the site. However, sensitive files should never be uploaded to a public S3 bucket.

Important security considerations:

- Do not upload passwords, API keys, or private documents.
- Only make required website files public.
- Review bucket permissions before publishing.
- Use clear folder and file names.
- Delete unused public files.
- Consider using Amazon CloudFront for improved security and performance.

---

## Future Improvements

This project can be improved by adding:

- Amazon CloudFront for content delivery
- HTTPS using CloudFront and AWS Certificate Manager
- A custom domain name using Amazon Route 53
- S3 bucket policy instead of manually changing object permissions
- Versioning for website file changes
- Logging for access tracking
- Infrastructure as Code using Terraform
- CI/CD deployment using GitHub Actions
- Error page configuration using `error.html`
- Improved website design with CSS and JavaScript

---

## Recommended Architecture Upgrade

For a more production-ready version of this project, the architecture could be improved like this:

```text
User Browser
     |
     | HTTPS
     |
Amazon CloudFront
     |
     | Origin Access Control
     |
Amazon S3 Bucket
     |
     | Static Website Files
     |
index.html + CSS + JavaScript + Images
```

This would improve:

- Security
- Performance
- Global availability
- HTTPS support
- Caching
- Professional deployment quality

---

## Cost Management

Amazon S3 is generally low cost for static website hosting, but charges may apply for:

- Storage
- Requests
- Data transfer
- Optional services such as CloudFront or Route 53

To avoid unnecessary charges:

1. Delete unused files.
2. Empty the S3 bucket if the project is no longer needed.
3. Delete the S3 bucket after testing.
4. Review AWS billing alerts.

---

## Cleanup

To clean up the project:

1. Go to the S3 console.
2. Open the bucket.
3. Delete all uploaded files.
4. Delete all uploaded folders.
5. Disable static website hosting if needed.
6. Delete the S3 bucket.

---

## Project Completion Time

This project took approximately 45 minutes to complete.

---

## Conclusion

This project demonstrates how Amazon S3 can be used to host a static website without managing servers.

By creating an S3 bucket, uploading website files, enabling static website hosting, configuring public access, and troubleshooting permission errors, I gained hands-on experience with AWS storage and static website hosting.

This project highlights foundational cloud skills relevant to:

- Cloud Support
- AWS Administration
- Web Hosting
- Technical Support
- Cloud Engineering
- DevOps Fundamentals
