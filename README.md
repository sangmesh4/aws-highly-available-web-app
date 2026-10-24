
# 🏦 AWS QuickLoan Site-Portal

### ☁️ A Highly Available, Auto-Scaling, 3-Tier Web Application on AWS

> **Build • Deploy • Scale • Monitor**
> 🚀 A hands-on AWS Cloud & DevOps project demonstrating secure networking, web application hosting, database integration, high availability, auto scaling, and monitoring.

---

## 📑 Table of Contents

1. [📖 Project Overview](#1--project-overview)
2. [🎯 Project Objectives](#2--project-objectives)
3. [✨ Key Features](#3--key-features)
4. [🧰 Technology Stack](#4--technology-stack)
5. [🏗️ Architecture Highlights](#5--architecture-highlights)
6. [💼 Project Summary](#6--project-summary)

---

## 1. 📖 Project Overview

### 🔍 About the Project

**AWS QuickLoan Site-Portal** is a hands-on cloud project that deploys a loan application website on AWS using a **highly available, secure, and scalable 3-tier architecture**.

The application runs on **Nginx and PHP web servers** inside a custom **Amazon VPC** with public and private subnets. The **MySQL database** is hosted on Amazon RDS in a private network configuration without public access.

Administrative access to private servers is provided through a **Jump Server (Bastion Host)**, while static application images are stored in **Amazon S3**.

An **Application Load Balancer (ALB)** distributes incoming application traffic across web servers, and **EC2 Auto Scaling** adjusts the number of application instances based on demand.

Finally, **Amazon CloudWatch** monitors application infrastructure, while **Amazon SNS** delivers email notifications when CPU utilization crosses configured thresholds.

### 🏗️ Architecture at a Glance

```text
                         👤 USER / BROWSER
                                |
                                ▼
                       🌍 CUSTOM DOMAIN
                                |
                                ▼
                  ⚖️ APPLICATION LOAD BALANCER
                                |
                 ┌──────────────┴──────────────┐
                 ▼                             ▼
          🖥️ WEB SERVER 1                🖥️ WEB SERVER 2
          Nginx + PHP                    Nginx + PHP
                 │                             │
                 └──────────────┬──────────────┘
                                |
                  ┌─────────────┴─────────────┐
                  ▼                           ▼
          🗄️ AMAZON RDS                 🪣 AMAZON S3
          MySQL Database                Static Images
          Private Network
                                
                  📈 EC2 AUTO SCALING
                          |
                          ▼
                 📊 AMAZON CLOUDWATCH
                          |
                          ▼
                    📧 AMAZON SNS
                    Email Alerts
```

**🔐 Network Foundation:** Custom VPC · Public Subnets · Private Subnets · Internet Gateway · NAT Gateway · Route Tables · Security Groups · Bastion Host

---

## 2. 🎯 Project Objectives

The primary objective is to build and deploy a cloud-based web application using AWS services and fundamental cloud engineering practices.

* 🔐 **Secure Network Architecture** — Build a custom VPC with public and private subnets, an Internet Gateway (IGW), a NAT Gateway, and a Bastion Host.
* 🖥️ **Web Application Hosting** — Host a PHP-based loan application using Nginx and connect it to a private MySQL database.
* 🗄️ **Database Integration** — Configure Amazon RDS for MySQL and establish connectivity between the application and database.
* 🪣 **Static Asset Management** — Store application images in Amazon S3 to reduce the need to keep static assets on application servers.
* ⚖️ **High Availability** — Use an Amazon Machine Image (AMI), Launch Template, Application Load Balancer, and Auto Scaling Group.
* 📈 **Automatic Scaling** — Configure scaling policies to add or remove application instances according to CPU utilization.
* 📊 **Infrastructure Monitoring** — Monitor application infrastructure and CPU metrics using Amazon CloudWatch.
* 📧 **Automated Notifications** — Configure Amazon SNS to deliver email alerts when monitoring thresholds are breached.

---

## 3. ✨ Key Features

|  #  | Feature                      | Implementation                | Key Benefit                                                                     |
| :-: | ---------------------------- | ----------------------------- | ------------------------------------------------------------------------------- |
|  1  | 🛡️ Bastion Host Access      | Jump Server / Bastion Host    | Provides a controlled administrative entry point to private servers.            |
|  2  | 🔐 Private Network           | VPC, Public & Private Subnets | Separates public-facing resources from private infrastructure.                  |
|  3  | 🗄️ Private Database         | Amazon RDS for MySQL          | Keeps the database off the public internet.                                     |
|  4  | 🌐 Web Application Hosting   | Nginx + PHP 8.2               | Serves the loan application website.                                            |
|  5  | 🪣 Static Asset Storage      | Amazon S3                     | Stores and serves application images.                                           |
|  6  | ⚖️ Load Balancing            | Application Load Balancer     | Distributes incoming application traffic across registered targets.             |
|  7  | 📈 Auto Scaling              | EC2 Auto Scaling Group        | Automatically adjusts the number of instances according to configured policies. |
|  8  | 🔺 CPU Scale-Out             | CloudWatch Alarm: CPU > 80%   | Triggers a scaling action to add an instance.                                   |
|  9  | 🔻 CPU Scale-In              | CloudWatch Alarm: CPU < 20%   | Triggers a scaling action to remove an instance.                                |
|  10 | 📧 Email Notifications       | Amazon SNS                    | Sends email notifications for configured monitoring alarms.                     |
|  11 | 🌍 Custom Domain             | `quickloan.hopto.org`         | Makes the application accessible through a domain name.                         |
|  12 | 📊 Infrastructure Monitoring | Amazon CloudWatch             | Monitors metrics and evaluates configured alarms.                               |

> 💡 **Important:** The CPU thresholds above represent the project's configured scaling policies. Actual scaling behavior also depends on alarm evaluation periods, scaling configuration, and cooldown or instance warm-up settings.

---

## 4. 🧰 Technology Stack

The project combines AWS cloud infrastructure, Linux administration, web technologies, storage, networking, and monitoring.

### ☁️ AWS Cloud Services

| Service                                | Purpose                                                                  |
| -------------------------------------- | ------------------------------------------------------------------------ |
| 🌐 **Amazon VPC**                      | Creates an isolated virtual network.                                     |
| 🧩 **Amazon EC2**                      | Hosts the web application and jump server.                               |
| ⚖️ **Application Load Balancer (ALB)** | Distributes incoming HTTP/HTTPS traffic.                                 |
| 📈 **EC2 Auto Scaling**                | Adjusts the number of application instances.                             |
| 🗄️ **Amazon RDS for MySQL**           | Provides managed relational database hosting.                            |
| 🪣 **Amazon S3**                       | Stores static application images.                                        |
| 📊 **Amazon CloudWatch**               | Collects metrics and evaluates alarms.                                   |
| 📧 **Amazon SNS**                      | Sends email notifications.                                               |
| 🌍 **Internet Gateway (IGW)**          | Enables internet connectivity for appropriately routed public resources. |
| 🚪 **NAT Gateway**                     | Enables outbound internet connectivity for private-subnet resources.     |
| 🖼️ **Amazon Machine Image (AMI)**     | Provides a reusable instance image.                                      |
| 🚀 **Launch Template**                 | Defines the configuration used to launch EC2 instances.                  |
| 🎯 **Target Group**                    | Defines the targets and health checks used by the load balancer.         |

### 🖥️ Operating System & Web Technologies

| Technology                 | Purpose                                                  |
| -------------------------- | -------------------------------------------------------- |
| 🐧 **Amazon Linux**        | Operating system for EC2 instances.                      |
| 🌐 **Nginx**               | Web server and reverse proxy.                            |
| 🐘 **PHP 8.2**             | Application runtime.                                     |
| 🗄️ **MySQL**              | Relational database engine.                              |
| 🔗 **PHP MySQLi**          | Connects the PHP application to the MySQL database.      |
| 🌍 **Custom Domain / DNS** | Provides a domain name for application access.           |
| 🔑 **SSH**                 | Enables secure administrative access to Linux instances. |

### 🏷️ Quick Technology Stack

`AWS VPC` · `EC2` · `ALB` · `Auto Scaling` · `S3` · `RDS MySQL` · `CloudWatch` · `SNS` · `Nginx` · `PHP 8.2` · `Amazon Linux` · `SSH` · `DNS`

---

## 5. 🏗️ Architecture Highlights

### 🔹 5.1 Secure Networking

* Create a custom VPC.
* Configure public and private subnets.
* Attach an Internet Gateway.
* Configure a NAT Gateway and Elastic IP.
* Associate route tables with the appropriate subnets.
* Use security groups to control network access.

### 🔹 5.2 Application & Database

* Install Nginx and PHP on the web servers.
* Deploy the loan application files.
* Store static images in Amazon S3.
* Configure Amazon RDS for MySQL.
* Connect the PHP application to the database.
* Configure the application domain in DNS and Nginx.

### 🔹 5.3 High Availability & Scaling

* Create an AMI from the configured application server.
* Build a Launch Template.
* Configure an Application Load Balancer and Target Group.
* Create an Auto Scaling Group.
* Configure CPU-based scale-out and scale-in policies.

### 🔹 5.4 Monitoring & Notifications

* Configure Amazon CloudWatch alarms.
* Monitor CPU utilization for the Auto Scaling Group.
* Create an Amazon SNS topic.
* Subscribe an email endpoint to the topic.
* Connect alarm notifications to SNS.

---

## 6. 💼 Project Summary

### 🚀 Resume-Ready Project Description

> Designed and deployed a loan application portal on AWS using a custom VPC with public and private subnets, an Internet Gateway, NAT Gateway, and Bastion Host. Hosted a PHP/Nginx web application integrated with a private Amazon RDS MySQL database and Amazon S3 for static asset storage. Implemented an Application Load Balancer and EC2 Auto Scaling policies for traffic distribution and dynamic capacity management, with Amazon CloudWatch monitoring and Amazon SNS email notifications for CPU-based alarms.

### 🎯 Skills Demonstrated

* ☁️ AWS Cloud Infrastructure
* 🌐 VPC & Networking
* 🐧 Linux System Administration
* 🖥️ Nginx & PHP Application Hosting
* 🗄️ MySQL & Amazon RDS Integration
* 🪣 Amazon S3 Storage
* ⚖️ Load Balancing & Auto Scaling
* 📊 Monitoring & Alerting
* 🔐 Network Security Fundamentals
* 🚀 Cloud Application Deployment

---

<div align="center">

### ⭐ Build • Deploy • Scale • Monitor ⭐

**AWS Cloud | Linux | Networking | Web Hosting | Database | Monitoring**

*Learning cloud engineering through practical, real-world infrastructure projects.*

</div>
