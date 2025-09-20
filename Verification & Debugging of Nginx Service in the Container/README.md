📂Project Setup

mkdir my-static-site

cd my-static-site

mkdir site

cd site

vim index.html       # added "Hello from Docker + nginx"

cd ..

nano Dockerfile     # wrote Dockerfile with ubuntu + nginx

<img width="1728" height="750" alt="image" src="https://github.com/user-attachments/assets/0947a731-4509-42db-92e3-9ed352d488d9" />

Dockerfile

<img width="741" height="661" alt="image" src="https://github.com/user-attachments/assets/ffff36f4-f547-461e-a983-58c0b187c733" />



🐳 Build Docker Image

docker build -t static-ubuntu-nginx:latest .

🚀 Run Container

docker run -d --name site-ubuntu -p 8080:80 static-ubuntu-nginx:latest

docker ps --filter name=site-ubuntu

<img width="1909" height="753" alt="image" src="https://github.com/user-attachments/assets/4e595e03-98a0-4932-9b84-2c1d3fb4119d" />

🔍 Verify Nginx

docker exec -it site-ubuntu sh -c "command -v nginx; nginx -v"

<img width="1458" height="365" alt="image" src="https://github.com/user-attachments/assets/4bc6ca5f-d414-4a14-b5a3-18317b5f4afa" />

🌐 Open Website

Visit in browser:

👉 http://localhost:8080

You can see:

<img width="1844" height="907" alt="image" src="https://github.com/user-attachments/assets/6d22bcc8-1fa6-4946-a0dc-5a605d2eac4d" />

“Hello from Docker + nginx”
