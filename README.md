# AWS Web Server Project

![AWS](https://img.shields.io/badge/AWS-Cloud-brightgreen) ![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white) ![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

This repository contains the source code and deployment instructions for an **AWS-based web server**. The web server is designed to host a simple application (e.g., a static website, REST API, or dynamic web app) using AWS services such as EC2, S3, and optionally RDS or CloudFront.

---

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Prerequisites](#prerequisites)
4. [Installation](#installation)
5. [Deployment](#deployment)
6. [Contact](#contact)

---

## Overview

This project demonstrates how to deploy a web server on AWS using **Amazon EC2** instances. The web server can serve static content (e.g., HTML, CSS, JavaScript) or act as a backend for dynamic applications (e.g., Flask, Django, Node.js). It leverages AWS services like **S3** for storage, **RDS** for databases (optional), and **CloudFront** for content delivery (optional).

---

## Features

- **Scalable**: Deployed on AWS EC2 for scalability.
- **Secure**: Configured with security groups and IAM roles.
- **Customizable**: Supports static websites, APIs, or full-stack applications.
- **Automated Deployment**: Includes scripts for automating setup and deployment.
- **Cost-Effective**: Optimized for AWS Free Tier usage.

---

## Prerequisites

Before you begin, ensure you have the following:

- An **AWS account** with appropriate permissions.
- **AWS CLI** installed and configured (`aws configure`).
- **SSH Key Pair** for accessing EC2 instances.
- Basic knowledge of:
  - AWS services (EC2, S3, etc.)
  - Linux commands
  - Your chosen programming language/framework (e.g., Python, Node.js)

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/<repository-name>.git
cd <repository-name>
```
---
## Deployment

### 1. Launch an EC2 Instance

```
aws ec2 run-instances \
    --image-id ami-0c55b159cbfafe1f0 \  # Ubuntu 20.04 LTS AMI
    --instance-type t2.micro \
    --key-name <your-key-pair> \
    --security-group-ids <security-group-id> \
    --subnet-id <subnet-id> \
    --count 1 \
    --tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=WebServer}]'
```
### 2. SSH into the Instance
```
ssh -i /path/to/<your-key-pair>.pem ubuntu@<public-ip-address>
```
### 3. Set up the web server
```
bash setup.sh

setup.sh
sudo apt update
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx

```
### 4. Deploy the application
```
scp -i /path/to/<your-key-pair>.pem -r ./app/* ubuntu@<public-ip-address>:/var/www/html/
sudo systemctl restart nginx
```
### 5. Test connection
Once deployed, access your web server via the public IP address or domain name:
```
http://<public-ip-address>
```
You could also test it from the command line
```
curl http://<public-ip-address>/api/example
```
---

## Contact
For questions or feedback, feel free to reach out:
- GitHub : @prakash-cloud-1987
- Email : prakashrange1987@gmail.com
---


