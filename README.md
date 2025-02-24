# Secure-Web-Server-with-User-Access-Control
I set up an NGINX web server inside a Docker container running on Ubuntu (inside a Windows environment). I'll then implement user access controls using Linux users, groups, and permissions.
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
