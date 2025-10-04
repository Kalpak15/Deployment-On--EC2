<div align="center">
  
# 🚗 Ride Buddy
## Smart Ride-Sharing Platform
  
*Community-Driven Transportation • Secure Connections • Seamless Experience*
  
  [![React](https://img.shields.io/badge/React-18.x-61dafb.svg)](https://reactjs.org/)
  [![Express](https://img.shields.io/badge/Express-4.x-green.svg)](https://expressjs.com/)
  [![MongoDB](https://img.shields.io/badge/MongoDB-Latest-green.svg)](https://mongodb.com/)
  [![JWT](https://img.shields.io/badge/JWT-Authentication-orange.svg)](https://jwt.io/)
</div>

## 🚀 Overview

*Ride Buddy* is a cutting-edge full-stack web application designed to revolutionize ride-sharing by seamlessly connecting drivers and passengers. Built for modern communities, universities, and urban areas, Ride Buddy creates a trusted ecosystem where transportation becomes efficient, affordable, and socially connected through intelligent matching and secure payment processing.


# Project Deployment on AWS EC2

This guide provides step-by-step instructions for deploying a full-stack application on AWS EC2 instance.

## Table of Contents
- [Prerequisites](#prerequisites)
- [EC2 Instance Setup](#ec2-instance-setup)
- [Project Setup](#project-setup)
- [Backend Deployment](#backend-deployment)
- [Frontend Deployment](#frontend-deployment)
- [Demo & Screenshots](#demo--screenshots)
- [Troubleshooting](#troubleshooting)

---

## Prerequisites

Before starting the deployment, ensure you have:
- AWS Account with EC2 access
- SSH key pair (.pem file) for EC2 access
- Your project repository URL
- Basic knowledge of terminal/command line

---

## EC2 Instance Setup

### Step 1: Launch EC2 Instance

1. Log in to AWS Console
2. Navigate to *EC2 Dashboard*
3. Click *Launch Instance*
4. Configure instance:
   - *Name*: Give your instance a meaningful name
   - *AMI*: Select Ubuntu Server 22.04 LTS (or your preferred OS)
   - *Instance Type*: t2.micro (free tier) or t2.medium (recommended for better performance)
   - *Key Pair*: Create new or select existing key pair
   - *Storage*: 20 GB minimum
5. Click *Launch Instance*

### Step 2: Connect to EC2 Instance

1. Go to *EC2 Dashboard*
2. Select your instance
3. Click *Connect* button at the top
4. Choose *EC2 Instance Connect* tab
5. Click *Connect* button
6. A new browser window will open with terminal access

### Step 3: Update System Packages

bash
sudo apt update
sudo apt upgrade -y


---

## Project Setup

### Step 1: Install Node.js and npm

bash

# Download and install nvm:
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
# in lieu of restarting the shell
\. "$HOME/.nvm/nvm.sh"
# Download and install Node.js:
nvm install 24
# Verify the Node.js version:
node -v # Should print "v24.9.0".
# Verify npm version:
npm -v # Should print "11.6.0".



### Step 2: Install Git (if not already installed)

bash
sudo apt install git -y
git --version


### Step 3: Clone Your Project

bash
# Navigate to home directory
cd ~

# Clone your repository
git clone "https://github.com/your-username/your-repository.git"

# Navigate to project directory
cd your-repository


---


## Database Setup (MongoDB)


# Import MongoDB GPG key
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg --dearmor

# Add MongoDB repository
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list

# Update packages
sudo apt update

# Install MongoDB
sudo apt install -y mongodb-org

# Start MongoDB service
sudo systemctl start mongod
sudo systemctl enable mongod

# Verify MongoDB is running
sudo systemctl status mongod


## Backend Deployment

### Step 1: Install Backend Dependencies

bash
# Navigate to backend directory
cd backend

# Install npm packages
npm install


### Step 2: Configure Environment Variables

bash
# Create .env file
DATABASE_URL="mongodb://localhost:27017/Ride_Buddy"
CLOUDINARY_CLOUD_NAME= YOUR_ClOUDINARY_URL
CLOUDINARY_API_KEY=  YOUR_ClOUDINARY_KEY
CLOUDINARY_API_SECRET= YOUR_ClOUDINARY_SECRET
PORT=3000
JWT_SECRET_KEY=YOUR_KEY
EMAIL_USER=YOUR_EMAIL
EMAIL_PASSWORD=EMAIL_PASSWORD
key_id=RAZORPAY_KEY_ID    # for Payment Gateway
key_secret=RAZORPAY_KEY_SECRET


### Step 3: Configure Security Groups for Backend

1. Go to *EC2 Dashboard* → *Security Groups*
2. Select your instance's security group
3. Click *Edit inbound rules*
4. Add the following rules:
   - *Type*: Custom TCP
   - *Port*: 3000 (or your backend port)
   - *Source*: 0.0.0.0/0 (or specific IPs for security)
5. Click *Save rules*


### Step 4: start Backend

bash
npm start



## Frontend Deployment

### Step 1: Update Frontend Configuration

bash
# Navigate to frontend directory
cd ~/your-repository/frontend



### Step 2: Install Frontend Dependencies

bash
# Install npm packages
npm install


### Step 3: Configure Environment Variables

#create env
nano .env

VITE_key_id=YOUR_KEY_ID
VITE_key_secret=YOUR_SECRET
VITE_API_URL==http://your-ec2-public-ip:3000



### Step 4: Configure Security Groups for Frontend

1. Go to *EC2 Dashboard* → *Security Groups*
2. Select your instance's security group
3. Click *Edit inbound rules*
4. Add the following rules:
   - *Type*: Custom TCP
   - *Port*: 5173 (or your frontend port)
   - *Source*: 0.0.0.0/0 (or specific IPs for security)
5. Click *Save rules*
---


### Step 5: start Frontend

bash
nohup npm run dev -- --host &



## Demo & Screenshots

### Application Access

- *Frontend URL*: http://your-ec2-public-ip
- *Backend API*: http://your-ec2-public-ip:3000

### Screenshots

Screenshots are added in Above Screenshots Folder


### Demo Video

[Link to your demo video](https://drive.google.com/file/d/1g9FgRwZcNn4YHgMUzo4I0FCj6GFXL5ae/view?usp=sharing)




## Author

Kalpak Kulkarni - [GitHub Profile](https://github.com/Kalpak15)

## License

This project is licensed under the MIT License - see the LICENSE file for details.



*⭐ If Ride Buddy helps you, please consider starring this repository!*

Made with ❤ for smarter transportation everywhere



🌟 *Star this project* • 🐛 *Report Bug* • 💡 *Request Feature* • 🤝 *Contribute*

Transforming transportation, one ride at a time

</div>


## 📄 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
