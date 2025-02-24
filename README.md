# 🚀 Secure Web Server with User Access Control using Docker & Ubuntu

## **📌 Project Overview**
This project demonstrates how to set up an **NGINX web server** inside a **Docker container running on Ubuntu** while implementing **user access controls**. The goal is to showcase skills in **networking, IAM (Identity and Access Management), and Docker containerization**.

## **📂 Project Structure**
3️⃣ Build the Docker Image

docker build -t my-nginx-server .

4️⃣ Run the Container

docker run -d -p 8080:80 --name nginx-container my-nginx-server

5️⃣ Verify the Running Container

docker ps


🌍 Access the Web Server
Open your browser and visit:
👉 http://localhost:8080

If NGINX is running correctly, you should see the default welcome page.

🔑 Implementing Access Control

1️⃣ Enter the Container Shell

docker exec -it nginx-container bash

2️⃣ Create a User Group & Users

groupadd webadmins

groupadd webviewers

useradd -m -G webadmins adminuser
useradd -m -G webviewers vieweruser
Set passwords for the users:


echo "adminuser:password123" | chpasswd
echo "vieweruser:password123" | chpasswd

3️⃣ Restrict Access to a Secure Directory
Open the NGINX config file:

nano /etc/nginx/nginx.conf
Add this inside the server block:
nginx

location /secure {
    auth_basic "Restricted Content";
    auth_basic_user_file /etc/nginx/.htpasswd;
}
Save and exit.

4️⃣ Create a Password File

apt update && apt install -y apache2-utils

htpasswd -c /etc/nginx/.htpasswd adminuser

Enter a secure password for adminuser.

5️⃣ Restart NGINX

systemctl restart nginx

✅ Testing the Authentication

Open http://localhost:8080/secure in a browser.

A login prompt should appear.

Enter the adminuser credentials.

If correct, you should be able to access the secure content.

📸 Screenshots (Optional)
Add images of:

The running container (docker ps output)
The NGINX welcome page
The login authentication prompt
📖 What You Learned
How to run an NGINX server inside a Docker container.
How to set up IAM using Linux users and groups.
How to apply basic authentication with NGINX.
How to manage and secure access to web resources.
🚀 Future Improvements
Use Docker Compose to simplify setup.
Implement SSL encryption for secure connections.
Automate user provisioning using scripts.
