# AWS Cloud Resume Challenge ☁️📄

![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?style=for-the-badge&logo=amazon-dynamodb&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)

**Live Demo:** www.fezanahmed.co.uk

---

## 📖 Overview
This project is a serverless, full-stack web application built on AWS to host my professional resume. It demonstrates cloud engineering skills including **Serverless architecture**, **CI/CD pipelines**, and **NoSQL databases**.

## 🏗️ Architecture
![Architecture Diagram](architecture-diagram.png)

The application follows a decoupled serverless architecture:

### **1. Frontend (Static Website)**
* **Amazon S3:** Hosts the HTML, CSS, and JavaScript assets.
* **Amazon CloudFront:** Functions as a global Content Delivery Network (CDN) to cache the site closer to users and enforce HTTPS security.
* **Route 53:** Manages DNS records and points the custom domain to the CloudFront distribution.

### **2. Backend (Visitor Counter API)**
* **AWS Lambda (Python):** A serverless function that handles the logic for retrieving and updating the visitor count.
* **Amazon DynamoDB:** A NoSQL database that stores the atomic visitor count.
* **Amazon API Gateway:** Exposes a RESTful API endpoint that triggers the Lambda function from the frontend JavaScript.

### **3. Automation (CI/CD)**
* **GitHub Actions:**
    * **Frontend Pipeline:** Automatically syncs changes to the S3 bucket and invalidates the CloudFront cache when code is pushed to the `main` branch.
    * **Backend Pipeline:** Runs Python tests and updates the Lambda function code automatically.

---

## 🛠️ Tech Stack

| Component | Technology | Description |
| :--- | :--- | :--- |
| **Frontend** | HTML5, CSS3, JavaScript | Static resume content and API integration script. |
| **Hosting** | S3 & CloudFront | Secure, high-availability global hosting. |
| **Compute** | AWS Lambda (Python 3.9) | Serverless execution for the API logic. |
| **Database** | DynamoDB | Key-Value store for the visitor counter. |
| **API** | API Gateway | REST API interface for the backend. |
| **CI/CD** | GitHub Actions | Automated testing and deployment pipelines. |
| **Source Control** | Git & GitHub | Version control. |

---

## 🚀 Key Features
* **Global Distribution:** Low-latency access worldwide via CloudFront edge locations.
* **Secure HTTPS:** Enforced via ACM (AWS Certificate Manager) SSL certificates.
* **Atomic Counting:** Ensures the visitor count remains accurate even with concurrent traffic using DynamoDB atomic updates.
* **Automated Deployments:** Zero-touch deployment; committing code updates the live infrastructure instantly.
* **Cost Optimized:** Designed to run entirely within the AWS Free Tier limitations.

---

## 🧠 Design Decisions & Trade-offs

### **Why DynamoDB over RDS?**
I chose DynamoDB because the data structure (a single key-value pair for the count) is extremely simple. Provisioning a full SQL instance (RDS) would be overkill, expensive, and require ongoing patching/maintenance. DynamoDB's on-demand scaling fits the serverless model perfectly.

### **Why CloudFront?**
While S3 can host static sites directly, it only supports HTTP. CloudFront was necessary to provide **SSL/HTTPS** security (a requirement for modern web standards) and to improve load times for users geographically distant from the S3 bucket's region.

---

## 🏆 Certifications
* AWS Certified Cloud Practitioner

---

_This project was built as part of the [Cloud Resume Challenge](https://cloudresumechallenge.dev/)._
