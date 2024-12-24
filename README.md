# AltSchool 2nd Semester Final Project: Deploying GitHub Web Page on AWS EC2 Server
Submitted By: Osagie Anolu     ALT/SOE/024/0317
Course: Cloud Engineering Karatu '24

# Project Overview
This document details the step-by-step process of provisioning an AWS EC2 server, installing and configuring an Apache web server, deploying an HTML project from GitHub, and securing the website (osagieanolu.enginner) Certbot for SSL/HTTPS.

# Table of Contents
- Server Provisioning on AWS EC2
- Accessing the EC2 Instance via SSH
- Installing and Configuring Apache Server
- Deploying the GitHub Project Files
- Configuring SSL with Certbot
- Redirecting HTTP to HTTPS
- Verification and Testing
- Conclusion and Website URL

# Server Provisioning on AWS EC2
- Logged into the AWS Management Console.
- Created a new EC2 instance with the following configuration:
- AMI: Ubuntu Server 22.04 LTS
- Instance Type: t2.micro (Free Tier)
- Key Pair: I used an existing one for SSH access.
- Security Group: Allowed inbound rules for HTTP (port 80), HTTPS (port 443), and SSH (port 22).
- Launched the instance successfully and noted its Public IP Address: 3.84.13.68
- Accessing the EC2 Instance via SSH
- Opened a terminal and connected to the server using SSH:
- ssh -i my-aws-key.pem ubuntu@3.84.13.68
- Switched to the root user: sudo -I
- Installing and Configuring Apache Server
- Updated the server:
- apt update -y
- Installed Apache Web Server:
- apt install -y apache2
- Verified Apache status:
- systemctl status apache2
- Enabled Apache to start on boot:
- systemctl enable apache2
- Deploying the GitHub Project Files
- Created a project directory:
- mkdir Landing-page 
- cd landing-page
- Downloaded the project files from GitHub:
- https://github.com/nolunchbreaks/landing-page/archive/refs/heads/main.zip
- Installed unzip and extracted the files:
- apt install unzip  
- unzip main.zip
- Moved the files to Apache’s root directory:
- cd Landing-page
- mv * /var/www/html/  
- cd /var/www/html/  
- ls -lrt
- 5. Restarted Apache to reflect changes:
- systemctl restart apache2

# Domain and SSL certificate
- I got a domain (osagieanolu.engineer) from name.com and I linked my IP addr to it
-  I installed Snapd-----apt install Snapd
- Installed certbot via snap-------sudo snap install --classic certbot
- Prepare Certbot Command------sudo certbot --apache
- Follow Certbot Prompts
   - Enter your email address.
    -Agree to the terms of service.
     -Choose whether to share your email with the EFF.
- Verify the Installation-------sudo certbot certificates
- Automate Renewal-------sudo crontab -e
   - 8. 0 0,12 * * * sudo certbot renew --quiet

# Conclusion
- The HTML project was successfully deployed on AWS EC2 and secured with SSL/TLS using Certbot.
- Secure URL: https://osagieanolu.engineer


![Screenshot (3)](https://github.com/user-attachments/assets/37684cf8-dd7c-4051-9159-ca56b1240323)


# Contact 
If you have any questions or suggestions, please feel free to open an issue or contact me by [email](mailto:osagieanolu22@gmail.com) or [LinkedIn](https://www.linkedin.com/in/osagie-anolu-963b78216/)
