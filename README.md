# 🚀 Node.js App Deployment on AWS EC2 using Nginx Reverse Proxy

**Author:** Prasad 👨‍💻  
**Project Type:** Full Deployment Guide  
**Platform:** AWS EC2 (Ubuntu)  
**Tech Stack:** Node.js + Express + Nginx  

---

## 🧠 Overview

This project demonstrates how to **deploy a Node.js application** on an **AWS EC2 Ubuntu instance** and use **Nginx as a reverse proxy server** to forward traffic from port 80 to your Node.js app (port 3000).

It’s a clean, production-ready setup widely used in real-world DevOps and Cloud deployments. ☁️⚙️

---

## ⚙️ Tech Stack

| Layer | Technology |
|-------|-------------|
| 🖥️ Backend | Node.js (Express.js) |
| 🌐 Web Server | Nginx |
| ☁️ Cloud Platform | AWS EC2 (Ubuntu 22.04) |
| 🧰 Process Manager | PM2 |

---

## 🪜 Deployment Steps

### 🧩 Step 1: Launch EC2 Instance
1. Go to **AWS Console → EC2 → Launch Instance**
2. Choose **Ubuntu 22.04 LTS**
3. Select instance type **t2.micro** (Free Tier)
4. Create or use an existing **Key Pair (.pem file)**
5. In **Security Group**, allow:
   - SSH (22)
   - HTTP (80)
   - Custom TCP (3000)
6. Launch your instance ✅

---

### 🧩 Step 2: Connect to EC2

```bash
ssh -i "your-key.pem" ubuntu@<EC2-Public-IP>

🧩 Step 3: Update Packages
sudo apt update -y && sudo apt upgrade -y

🧩 Step 4: Install Node.js & npm
sudo apt install -y nodejs
node -v
npm -v

🧩 Step 5: Create Node.js App
mkdir nodejs-proxy-app
cd nodejs-app
npm install

Create a file named index.js 👇

Run it:
node index.js

Check in browser:
http://<EC2-Public-IP>:3000

🧩 Step 6: Install and Configure Nginx
sudo apt install nginx -y
sudo systemctl enable nginx
Open Nginx config file:


sudo nano /etc/nginx/sites-available/default
Edit Nginx Configuration File:

Test configuration:
sudo nginx -t

Restart Nginx:
sudo systemctl restart nginx

✅ Now visit:
http://<EC2-Public-IP>
Your Node.js app is now accessible via port 80 through Nginx!

🧩 Step 7: Keep App Running After Logout
Install PM2 (process manager):
sudo npm install -g pm2
Start your app:
pm2 start index.js

pm2 list
pm2 startup systemd
pm2 save

📸 Recommended Screenshots 

1️⃣	EC2 Dashboard	Running instance details
2️⃣	Nginx Config File	/etc/nginx/sites-available/default
3️⃣	App on Port 80	After proxy setup
4️⃣ App on Port 3000
🧰 Folder Structure

nodejs-app/
├── index.js
├── package.json
├── package-lock.json
├── Images
└── README.md

🏁 Final Result
✅ Node.js app runs at:
http://<EC2-Public-IP>

✅ Traffic flows through:
Nginx → localhost:3000 → Node.js

✅ Managed with:
PM2 (auto-start on reboot)

🧑‍💻 Author
Prasad
🚀 Cloud & DevOps Learner | Node.js | AWS | Nginx | EC2
