# 🚀 Node.js App Deployment on AWS EC2 using Nginx Reverse Proxy

**Author:** Prasad 👨‍💻  
**Project Type:** Full Deployment Guide  
**Platform:** AWS EC2 (Ubuntu 22.04)  
**Tech Stack:** Node.js + Express + Nginx + PM2  

---
## 🌐 Overview:-

This guide demonstrates how to deploy a **Node.js application** on an **AWS EC2 Ubuntu instance** and use **Nginx as a reverse proxy** to forward traffic from **port 80** to your Node.js app running on **port 3000**.  

This setup ensures:-
- ✅ Production-ready deployment  
- ✅ Persistent running using **PM2**  
- ✅ Optimized traffic handling with **Nginx**  

---

## 📝 Prerequisites:-

- AWS Account with EC2 access  
- Basic knowledge of **Node.js, Nginx, and Linux commands**  
- SSH client (PowerShell, Terminal, or PuTTY)  
- Key Pair (.pem file) for EC2 access  
- Familiarity with **Ubuntu**

---

## ⚙️ Tech Stack:-

| Layer | Technology |
|-------|------------|
| 🖥️ Backend | Node.js (Express.js) |
| 🌐 Web Server | Nginx |
| ☁️ Cloud Platform | AWS EC2 (Ubuntu 22.04 LTS) |
| 🧰 Process Manager | PM2 |

---

## 🪜 Deployment Steps:-

### 1️⃣ Launch EC2 Instance:-

1. AWS Console → EC2 → Launch Instance  
2. Choose Ubuntu 22.04 LTS  
3. Instance type: t2.micro (Free Tier)  
4. Create/use Key Pair (.pem file)  
5. Security Group:
   - SSH (22)  
   - HTTP (80)  
   - Custom TCP (3000) for Node.js testing  
6. Launch instance  

### 2️⃣ Connect to EC2:-
```bash
ssh -i "your-key.pem" ubuntu@<EC2-Public-IP>
```
### 3️⃣ Update Packages:-
```
sudo apt update -y && sudo apt upgrade -y
```
### 4️⃣ Install Node.js & npm:-
```
sudo apt install -y nodejs npm
node -v
npm -v
```
### 5️⃣ Create Node.js App:-
```
mkdir nodejs-app
cd nodejs-proxy-app
npm install
```
### 6️⃣Create index.js:-
```
sudo nano index.js
```
### 7️⃣ Test the app:-
```
node index.js
```
- ***Visit: http://`<EC2-Public-IP>`:3000***

### 8️⃣ Install and Configure Nginx:-
```
sudo apt install -y nginx
sudo systemctl enable nginx
sudo systemctl start nginx
sudo nano /etc/nginx/sites-available/default
```
- ***Edit In Configure File:***

### 9️⃣ Test and restart:-
```
sudo nginx -t
sudo systemctl restart nginx
```
- ***Visit http://`<EC2-Public-IP>` to see your app running via Nginx on port 80.***

### 🔟 Keep App Running After Logout (PM2):-
```
sudo npm install -g pm2
pm2 start index.js
```

## 🧰 Folder Structure:-
```
nodejs-app/
├── index.js

├── package.json

├── README.md

└── Images (screenshots)
```
## 📸 Screenshots:-

| Screenshot        | Description                         |
|------------------|-------------------------------------|
| EC2 Dashboard     | Instance running details            |
| Nginx Config      | /etc/nginx/sites-available/default |
| App on Port 3000  | Before Nginx proxy setup            |
| App on Port 80    | After Nginx proxy setup   

## 🔄 Architecture Diagram:-

[ User ]

   ↓ HTTP (Port 80)
   
[ Nginx Reverse Proxy ]

   ↓ forwards to
   
[ Node.js App (Port 3000) ]

   ↓ Response sent back
   
[ User ]


## 🔑 Key Points:-

- ✅ Node.js app deployment on AWS EC2
- ✅ Traffic routed via Nginx reverse proxy
- ✅ Persistent app process using PM2
- ✅ Accessible publicly via HTTP Port 80
- ✅ Folder and configuration structure for production

## 📊 Benefits:-

- High availability on a single EC2 instance
- Production-ready setup with reverse proxy
- Persistent app process after SSH logout
- Easy maintenance and monitoring

## 💡 Notes & Tips:-

- Always use Key Pairs securely
- Adjust security group rules for your app port
- Test Node.js app before configuring Nginx
- Use PM2 startup to run app automatically on reboot

## 🏁 Final Result:-

- ✅ Node.js app hosted on AWS EC2
- ✅ Accessible via HTTP (Port 80
- ✅ Managed by Nginx reverse proxy
- ✅ Persistent with PM2

Example URL: http://`<EC2-Public-IP>`

## 👨‍💻 Author:-
Prasad
Cloud & DevOps Enthusiast | Node.js | AWS | Nginx | EC2

## 📩 Connect With Me :
If you’d like to collaborate, discuss projects, or just say hello — feel free to reach out!  

### 🔗 Social & Professional Links:-
- 🌐 [Portfolio Website](https://prasad-bhoite19.github.io/prasad-portfolio/)  
- 💼 [LinkedIn](http://linkedin.com/in/prasad-bhoite-a38a64223)  
- 🐙 [GitHub](https://github.com/Prasad-bhoite19)  
- ✉️ [Email](prasadsb2002@gmail.com)  

💬 Always open for opportunities in **Cloud, DevOps, and Full-Stack Projects**
