# 🔒 SSL Certificate Setup on AWS EC2 using Certbot

This repository documents the steps and configurations used to install and configure a **free SSL certificate** for a website hosted on an **AWS EC2 instance** using **Certbot** and **Let's Encrypt**. This project was implemented and tested by **Aryan Sharma**.

---

## 🌐 Overview

- Cloud Provider: **AWS EC2 (Ubuntu/Linux)**
- Web Server: **Apache2**
- Certificate Authority: **Let's Encrypt**
- Tool: **Certbot**
- Domain: Custom domain (configured with Route 53 or third-party DNS)

---

## 🛠️ Tech Stack

- **AWS EC2**
- **Apache2 Web Server**
- **Certbot (snap version)**
- **Let's Encrypt**
- **Custom Domain with DNS Configuration**

---

## ⚙️ Setup Steps

### 1. Connect to EC2 Instance

```bash
ssh -i your-key.pem ubuntu@your-ec2-public-ip
```

### 2. Update & Install Dependencies

```bash
sudo apt update
sudo apt install apache2 -y
sudo apt install snapd -y
sudo snap install core && sudo snap refresh core
```

### 3. Install Certbot

```bash
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```

### 4. Obtain SSL Certificate

```bash
sudo certbot --apache
```

- Enter your domain (e.g., `yourdomain.com`)
- Choose to redirect HTTP to HTTPS

### 5. Verify Renewal Cron Job

```bash
sudo certbot renew --dry-run
```

---

## 📁 Example Apache Config Path

```bash
/etc/apache2/sites-available/000-default.conf
/etc/letsencrypt/live/yourdomain.com/
```

You can check or update SSL certificates or virtual host settings here.

---

## ✅ Features

- Free HTTPS with Let’s Encrypt
- Auto-renewal configured
- Works with any domain name and Apache server
- Secures your site with TLS/SSL encryption

---

## 🛡️ Security Tips

- Open ports **80 (HTTP)** and **443 (HTTPS)** in your EC2 security group
- Regularly update system packages
- Use strong `.pem` key permissions (`chmod 400 your-key.pem`)

---

## 👨‍💻 Author

**Aryan Sharma**  
B.Tech CSE (AI & DS) | Poornima University  
GitHub: [@AryanSharma2206](https://github.com/AryanSharma2206)  
LinkedIn: [linkedin.com/in/aryan-sharma-a2a240353](https://www.linkedin.com/in/aryan-sharma-a2a240353)  
Location: Jaipur, India
