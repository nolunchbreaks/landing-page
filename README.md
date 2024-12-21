AltSchool 2nd Semester Final Project: Deploying GitHub Web Page on AWS EC2 Server
Submitted By: Osagie Anolu
Course: Cloud Engineering Karatu '24

Project Overview
This document details the step-by-step process of provisioning an AWS EC2 server, installing and configuring an Apache web server, deploying an HTML project from GitHub, and securing the website (osagieanolu.enginner) Certbot for SSL/HTTPS.
Table of Contents
1. Server Provisioning on AWS EC2
2. Accessing the EC2 Instance via SSH
3. Installing and Configuring Apache Server
4. Deploying the GitHub Project Files
5. Configuring SSL with Certbot
6. Redirecting HTTP to HTTPS
7. Verification and Testing
8. Conclusion and Website URL
1. Server Provisioning on AWS EC2
1. Logged into the AWS Management Console.
2. Created a new EC2 instance with the following configuration:
AMI: Ubuntu Server 22.04 LTS
Instance Type: t2.micro (Free Tier)
Key Pair: Generated a new key or used an existing one for SSH access.
Security Group: Allowed inbound rules for HTTP (port 80), HTTPS (port 443), and SSH (port 22).
3.Launched the instance successfully and noted its Public IP Address: 3.84.13.68

2. Accessing the EC2 Instance via SSH
1. Opened a terminal and connected to the server using SSH:

ssh -i my-aws-key.pem ubuntu@3.84.13.68
2. Switched to the root user:
sudo -I
3. Installing and Configuring Apache Server
1. Updated the server:
apt update -y
2. Installed Apache Web Server:
apt install -y apache2
3. Verified Apache status:
systemctl status apache2
4. Enabled Apache to start on boot:
systemctl enable apache2
4. Deploying the GitHub Project Files

1. Created a project directory:
mkdir Landing-page 
cd landing-page
2. Downloaded the project files from GitHub:
  https://github.com/nolunchbreaks/landing-page/archive/refs/heads/main.zip
3. Installed unzip and extracted the files:
apt install unzip  
unzip main.zip
4. Moved the files to Apache’s root directory:
cd Landing-page
mv * /var/www/html/  
cd /var/www/html/  
ls -lrt
5. Restarted Apache to reflect changes:
systemctl restart apache2
1.I got a domain (osagieanolu.engineer) from name.com and I linked my IP addr to it
2. Checked the SSL certificate status using an online tool (e.g., SSL Labs).
3. Ensured HTTP requests redirect to HTTPS automatically.
4. Conclusion and Website URL
The HTML project was successfully deployed on AWS EC2 and secured with SSL/TLS using AWS Certificate Manager (ACM) and Certbot.
Secure URL: https://osagieanolu.engineer


![WhatsApp Image 2024-12-21 at 11 42 11](https://github.com/user-attachments/assets/013fca60-cb53-481b-a20d-b1f9c94092b1)
