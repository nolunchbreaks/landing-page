# AltSchool 2nd Semester Final Project: Deploying GitHub Web Page on AWS EC2 Server
Submitted By: Osagie Anolu     ALT/SOE/024/0317
Course: Cloud Engineering Karatu '24

# Project Overview
This document details the step-by-step process of provisioning an AWS EC2 server, installing and configuring an Apache web server, deploying an HTML project from GitHub, and securing the website (osagieanolu.enginner) Certbot for SSL/HTTPS.

# Table of Contents
1. Server Provisioning on AWS EC2
2. Accessing the EC2 Instance via SSH
3. Installing and Configuring Apache Server
4. Deploying the GitHub Project Files
5. Configuring SSL with Certbot
6. Redirecting HTTP to HTTPS
7. Verification and Testing
8. Conclusion and Website URL

# Server Provisioning on AWS EC2
1. Logged into the AWS Management Console.
2. Created a new EC2 instance with the following configuration:
AMI: Ubuntu Server 22.04 LTS
Instance Type: t2.micro (Free Tier)
Key Pair: I used an existing one for SSH access.
Security Group: Allowed inbound rules for HTTP (port 80), HTTPS (port 443), and SSH (port 22).
3.Launched the instance successfully and noted its Public IP Address: 3.84.13.68
4. Accessing the EC2 Instance via SSH
5. Opened a terminal and connected to the server using SSH:
6. ssh -i my-aws-key.pem ubuntu@3.84.13.68
8. Switched to the root user: sudo -I
9. Installing and Configuring Apache Server
10. Updated the server:
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

Domain and SSL certificate
1.I got a domain (osagieanolu.engineer) from name.com and I linked my IP addr to it
2. I installed Snapd-----apt install Snapd
3. Installed certbot via snap-------sudo snap install --classic certbot
4. Prepare Certbot Command------sudo certbot --apache
5. Follow Certbot Prompts
  Enter your email address.
  Agree to the terms of service.
  Choose whether to share your email with the EFF.
6. Verify the Installation-------sudo certbot certificates
7. Automate Renewal-------sudo crontab -e
8. 0 0,12 * * * sudo certbot renew --quiet

The HTML project was successfully deployed on AWS EC2 and secured with SSL/TLS using Certbot.
Secure URL: https://osagieanolu.engineer


![WhatsApp Image 2024-12-21 at 11 42 11](https://github.com/user-attachments/assets/013fca60-cb53-481b-a20d-b1f9c94092b1)

# Contact 
If you have any questions or suggestions, please feel free to open an issue or contact me by [email](mailto:osagieanolu22@gmail.com) or [LinkedIn](https://www.linkedin.com/in/osagie-anolu-963b78216/)
