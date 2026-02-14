# Docker
🚀 Jenkins, Docker & Nginx on AWS EC2

Hands-on DevOps Infrastructure Setup

This project demonstrates a containerized DevOps environment built on AWS EC2 using Docker.
Instead of installing services directly on the host, all core components run as Docker containers, ensuring isolation, portability, and clean infrastructure management.

🧱 Architecture Overview
AWS EC2 (Ubuntu)
│
├── Docker Engine
│   ├── Jenkins (LTS) Container  → Port 8080
│   ├── Nginx Container          → Port 80
│   └── Ubuntu Container
│        ├── Python 3
│        └── Git
│        └── Custom Docker Image

⚙️ Tech Stack

Cloud: AWS EC2 (Ubuntu)

Containerization: Docker

CI/CD Tool: Jenkins (LTS)

Web Server: Nginx

Languages/Tools: Python 3, Git

OS: Linux (Ubuntu)

🔧 Implementation Steps
1️⃣ Install Docker (Official Script)
apt update
curl -fsSL https://get.docker.com -o install-docker.sh
sh install-docker.sh
docker -v

2️⃣ Run Jenkins Using Docker
docker run --name jenkinsvishal -d -p 8080:8080 jenkins/jenkins:lts


Jenkins UI accessible via:

http://<EC2-PUBLIC-IP>:8080

3️⃣ Retrieve Jenkins Initial Admin Password
docker exec -it jenkinsvishal cat /var/jenkins_home/secrets/initialAdminPassword


Completed Jenkins setup via browser

Created admin user and accessed Jenkins dashboard

4️⃣ Run Ubuntu Container & Create Custom Image
docker run -it ubuntu
apt update
apt install python3 git -y


Commit the running container as a custom image:

docker commit <container_id> vishal_image_from_container

5️⃣ Deploy Nginx Using Docker
docker run --name nginx_vishal -d -p 80:80 nginx


Nginx UI accessible via:

http://<EC2-PUBLIC-IP>

✅ Verification
docker ps
docker images


Jenkins running on port 8080

Nginx running on port 80

Custom Ubuntu image created successfully

💡 Key Learnings

Running CI/CD tools in containers keeps the host clean and maintainable

Docker enables fast setup, rollback, and portability

Jenkins + Docker is a strong foundation for scalable CI/CD pipelines

Ideal setup for experimenting with pipelines, agents, and cloud deployments

🚀 Next Enhancements

Jenkins Pipeline as Code (Jenkinsfile)

Docker-based Jenkins agents

Reverse proxy with Nginx

CI/CD deployment to cloud services

Volume persistence for Jenkins data

👨‍💻 Author

Vishal Ramesh Wagh
DevOps Engineer | Docker | Jenkins | AWS | CI/CD
