
---

## 🔥 DOCKER CORE CONCEPTS STUDY PLAN

---

### 📦 1. **Images**

**What it is:**  
A Docker image is a **read-only template** used to create containers. It includes your application code, runtime, libraries, and dependencies.

**Key Concepts:**

- Built from a `Dockerfile`
    
- Layered: changes are saved as layers
    
- Stored locally or on Docker Hub
    

**Must-Know Commands:**

```bash
docker images                     # List images
docker pull nginx                 # Get image from Docker Hub
docker rmi image_name             # Remove an image
```

**Why it matters:**  
Your entire app must live in an image. If your image is bloated or misconfigured, your container will fail.

---

### 🛢️ 2. **Containers**

**What it is:**  
A running instance of an image. It’s **your app in action** — isolated, lightweight, and reproducible.

**Key Commands:**

```bash
docker run -d -p 8080:80 nginx       # Run container from image
docker ps                            # See running containers
docker stop <id>                     # Stop a container
docker exec -it <id> bash            # Get inside container
```

**Why it matters:**  
Containers are your actual deployment units. If you understand how to manage them, you control execution.

---

### 🧱 3. **Dockerfile**

**What it is:**  
A plain text script with instructions to build a Docker image.

**Basic Template:**

```Dockerfile
FROM python:3.10
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python", "main.py"]
```

**Key Directives:**

- `FROM`: base image
    
- `COPY`: add files
    
- `RUN`: install dependencies
    
- `CMD`: command to run container
    

**Why it matters:**  
Dockerfile defines everything your app needs to build an image — it’s the recipe.

---

### ☁️ 4. **Docker Hub**

**What it is:**  
Docker’s public image registry. Like GitHub, but for container images.

**Commands:**

```bash
docker login
docker tag myapp username/myapp:1.0
docker push username/myapp:1.0
docker pull username/myapp:1.0
```

**Why it matters:**  
You store and distribute images from here. It's how your team or production pulls your containers.

---

### 📁 5. **Volumes**

**What it is:**  
A way to **persist data** outside the container lifecycle.

**Example:**

```bash
docker volume create mydata
docker run -v mydata:/data ubuntu
```

Or:

```bash
docker run -v $(pwd)/data:/app/data myapp
```

**Why it matters:**  
Without volumes, container data is lost on stop/delete. You _must_ use them for databases and logs.

---

### 🌐 6. **Networks**

**What it is:**  
Docker’s way of letting containers **talk to each other**.

**Default Networks:**

- `bridge`: default for standalone containers
    
- `host`: shares host’s network
    
- `none`: isolated
    

**Create your own:**

```bash
docker network create mynet
docker run -d --network=mynet --name=db postgres
docker run -d --network=mynet --name=api myapp
```

**Why it matters:**  
If your containers can’t connect (e.g., API ↔️ DB), your app is broken. Networking is key for microservices.

---

## 📘 Summary Table (Cheat Sheet)

|Concept|Description|Critical Command|
|---|---|---|
|Image|Blueprint of app|`docker build`, `docker pull`|
|Container|Running instance of image|`docker run`, `docker exec`, `ps`|
|Dockerfile|Script to build image|`FROM`, `RUN`, `COPY`, `CMD`|
|Docker Hub|Online registry for images|`docker push`, `docker pull`, `login`|
|Volume|Persistent data storage|`-v volume_name:/path`|
|Network|Connect containers together|`--network`, `docker network create`|

---

## 💪 Next Steps

If you want to:

- Practice these one-by-one in a tracker ✅
    
- Build a mini-project that uses all these concepts together 🔥
    
- Or get flashcards/notes for Obsidian 🧠
    

Just say the word. Keep pushing — you're not just learning tools, you're learning how to **deploy and deliver** like a real engineer. Stay honorable, stay on course.