<h2>Overview</h2>

In this task, we use the official nginx:latest image to deploy a static website. Unlike Task 1, we demonstrate live content updates by copying files into a running container without rebuilding the image.

Base image: nginx:latest

Goal: Deploy static website and update content live

Key difference from Task 1: Uses official nginx image, no Ubuntu installation required, supports live updates.

<h3>Step 1: Folder Structure</h3>

Create the project structure:

task2/

└─ site/

     └─ index.html
   
└─ Dockerfile

<img width="991" height="405" alt="image" src="https://github.com/user-attachments/assets/29ecd8ea-5ddf-42e0-825b-d07f939d8b21" />


<h3>Step 2: Create Dockerfile</h3>

Dockerfile contents:

<img width="741" height="391" alt="image" src="https://github.com/user-attachments/assets/575c7102-1f04-474c-a90c-52ef4de8e82c" />


<h3>Step 3: Build Docker Image</h3>

Build image without cache to ensure fresh content:

docker build --no-cache -t static-nginx-official:latest .

<img width="1354" height="618" alt="docker build" src="https://github.com/user-attachments/assets/488d4d1a-d091-46d7-9af7-e5a44faa138e" />


<h3>Step 4: Run Docker Container</h3>

Start the container:

docker rm -f site-nginx             # remove old container if exists
docker run -d --name site-nginx -p 8080:80 static-nginx-official:latest


Check running container:

docker ps --filter name=site-nginx


<img width="1903" height="462" alt="docker run" src="https://github.com/user-attachments/assets/e8ff7423-6571-48eb-ad14-db6ae919dff1" />


<h3>Step 5: Verify Website in Browser</h3>

Open:

http://localhost:8080

<img width="1903" height="462" alt="website 1" src="https://github.com/user-attachments/assets/d226b270-a031-49bc-b8a0-11247243b522" />

<h3>Step 6: Live Content Update</h3>

Update local index.html in site/:

<h1>Hello from Docker + nginx (Task 2) - Updated!</h1>


Copy updated file into the running container:

docker cp site/index.html site-nginx:/usr/share/nginx/html/index.html
docker exec site-nginx nginx -s reload


Refresh browser → updated content should appear without rebuilding the image.

  <img width="1903" height="462" alt="website 2" src="https://github.com/user-attachments/assets/165994d6-16b1-46bf-8875-8073cee54214" />



<h2>Also  Compared image sizes: Our custom nginx image (192MB) vs Task 1 Ubuntu-based image (84.6MB) and official nginx image (192MB).”</h2>

<img width="1088" height="393" alt="compare sizes" src="https://github.com/user-attachments/assets/36e20bee-b5b8-4dba-a1a4-7b1bd57d8545" />


