# 🚀 Jenkins and Web Server Deployment on Azure VM

This project demonstrates how to deploy and configure **Jenkins** and a simple **web application** on an **Ubuntu Azure Virtual Machine**, hosting both services on separate ports.
---

## 🧩 1. Project Overview
**Goal:**
* Host Jenkins on **port 8080**
* Host a simple HTML web page on **port 8081**
* Verify both services run simultaneously on the same VM
* Make them publicly accessible through **Azure NSG**
---

## 🧰 2. Prerequisites
* Azure account with permission to create resources
* Ubuntu 22.04 LTS Virtual Machine (minimum 2 GB RAM recommended)
* SSH access to the VM
* Basic understanding of Linux commands
---

## ⚙️ 3. Setting up Azure VM
1. Create an **Ubuntu 22.04 LTS** VM in Azure.
2. Allow inbound ports:
   * `22` → SSH
   * `8080` → Jenkins
   * `8081` → Web Server
3. Connect to your VM:
   ```bash
   ssh -i <your-key.pem> azureuser@<vm-public-ip>
   ```

---

## 🧱 4. Installing and Configuring Jenkins

Install Java and Jenkins:

```bash
sudo apt update -y
sudo apt install openjdk-17-jdk -y
```

Add Jenkins repository and install:

```bash
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt update -y
sudo apt install jenkins -y
```

Start Jenkins:
```bash
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```
---
## 🔑 5. Unlocking Jenkins

Get the initial admin password:
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Open Jenkins in your browser:
```
http://<vm-public-ip>:8080
```
* Paste the admin password
* Install suggested plugins
* Create your admin user

---

## 🌐 6. Deploying a Simple HTML Web Page

Create and host a basic web page:
```bash
mkdir ~/simple-web
cd ~/simple-web
nano index.html
```

Paste this HTML:
```html
<!DOCTYPE html>
<html>
<head>
  <title>Hello from Azure VM</title>
</head>
<body style="text-align:center; font-family:Arial;">
  <h1>Welcome to My Simple Web Page 🚀</h1>
  <p>Hosted on Ubuntu and running alongside Jenkins.</p>
</body>
</html>
```

Run the web server:
```bash
python3 -m http.server 8081
```

(Optional) Run in background:
```bash
nohup python3 -m http.server 8081 &
```
---

## 🔍 7. Verifying Running Services and Ports
Check running services:
```bash
systemctl list-units --type=service --state=running
```

Check open ports:
```bash
sudo ss -tuln
```

Find which process owns each port:
```bash
sudo lsof -i -P -n | grep LISTEN
```
---
## 🌎 8. Access in Browser

* Jenkins → `http://<vm-public-ip>:8080`
* Web App → `http://<vm-public-ip>:8081`

Make sure both ports (8080, 8081) are allowed in Azure NSG.
---

## 🧾 Author
**Manish Baranwal**
💼 IT Engineer | ☁️ Cloud & DevOps Enthusiast
📍 Hosted on: Azure | 🧰 Tools: Jenkins, Python, Ubuntu
[GitHub](https://github.com/manishbaranwal-51) | [LinkedIn](https://www.linkedin.com/in/manishbaranwal51/)
