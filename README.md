# 🐳 Docker Notes


# 1. ❓ What is Docker and why is it used in modern software development?

- Docker is a tool used to create, run, and manage applications inside containers.
- It is used because:
  - ✅ Applications run the same on every system
  - ✅ Easy deployment
  - ✅ Faster development
  - ✅ Lightweight compared to virtual machines
  - ✅ Helps in microservices architecture  

### 📌 Example:
A Java Spring Boot app can run the same on developer laptop, testing server, and production server.


# 2. 📦 What is the difference between a Docker image and a Docker container?

| Docker Image | Docker Container |
|---|---|
| Blueprint/template | Running instance of image |
| Read-only | Writable |
| Static | Dynamic |
| Used to create containers | Executes application |

### 📌 Example:

Image = Java application package  
Container = Running Java application  


# 3. ⚙️ How does Docker differ from virtual machines?

| Docker | Virtual Machine |
|---|---|
| Uses host OS kernel | Has separate OS |
| Lightweight | Heavy |
| Starts fast | Starts slower |
| Uses less memory | Uses more memory |



# 4. 📝 What is a Dockerfile and how do you write one?

 - Dockerfile is a text file containing instructions to build a Docker image.

### 📌 Example:

```dockerfile
FROM openjdk:17
COPY app.jar app.jar
CMD ["java", "-jar", "app.jar"]
```

---

# 5. 🛠️ What are common Dockerfile instructions?

## 🔹 FROM

- Defines base image.

example:

```dockerfile
FROM openjdk:17
```


## 🔹 RUN

```dockerfile
RUN apt-get update
```

- Executes command during image build.

example:

```dockerfile
RUN apt-get update
```

## 🔹 COPY

- Copies files into image.

example:

```dockerfile
COPY . /app
```

## 🔹 CMD

- Default command when container starts.

example:

```dockerfile
CMD ["java", "-jar", "app.jar"]
```

## 🔹 ENTRYPOINT

- Main executable command.

example:

```dockerfile
ENTRYPOINT ["java"]
```

# 6. 🔄 What is the difference between CMD and ENTRYPOINT?

| CMD | ENTRYPOINT |
|---|---|
| Can be overridden easily | Harder to override |
| Provides default arguments | Defines main command |

### 📌 Example:

```dockerfile
ENTRYPOINT ["java", "-jar"]
CMD ["app.jar"]
```


# 7. ⚡ How does Docker layer caching work?

- Each Dockerfile instruction creates a layer.
- Docker reuses unchanged layers from cache to speed up builds.

### 📌 Example:

- If only source code changes, dependency installation layer is reused.

---

# 8. 🚀 How do you optimize Docker image size?

- ✅ Use smaller base images  
- ✅ Remove unnecessary files  
- ✅ Use multi-stage builds  
- ✅ Combine RUN commands  
- ✅ Use .dockerignore  

### 📌 Example:

```dockerfile
FROM openjdk:17-jdk-slim
```


# 9. 🧩 What are multi-stage builds in Docker?

- Multi-stage builds use multiple FROM statements to reduce final image size.

### 📌 Example:

- ✅ First stage builds Java app  
- ✅ Second stage copies only JAR file  


# 10. 🚫 What is .dockerignore and why is it important?

- .dockerignore excludes unnecessary files from Docker build.

## 🎯 Benefits:

- ✅ Faster build  
- ✅ Smaller image  
- ✅ Better security  

### 📌 Example:

```dockerignore
target/
.git/
```

# 11. 🏗️ How do you build, tag, and push Docker images?

## 🔹 Build image

```bash
docker build -t myapp .
```

## 🔹 Tag image

```bash
docker tag myapp username/myapp:v1
```

## 🔹 Push image

```bash
docker push username/myapp:v1
```

---

# 12. 🌐 What is Docker Hub and what are private registries?

- Docker Hub is a public repository for Docker images.
- Private registry stores images privately inside company or organization.

### 📌 Example:

- ✅ Docker Hub  
- ✅ AWS ECR  
- ✅ JFrog Artifactory  

# 13. 🏷️ How do you manage Docker image versions and tags?

- Tags are used for versioning.

### 📌 Example:

```text
myapp:v1
myapp:v2
myapp:latest
```

## ✅ Best practice:

- Avoid only using latest.

---

# 14. 💾 What are Docker volumes and bind mounts?

## 🔹 Volumes

- Managed by Docker.

## 🔹 Bind mounts

- Connect host machine folder to container.

### 📌 Example:

```bash
docker run -v myvolume:/data
```

---

# 15. 📂 What is the difference between volumes, bind mounts, and tmpfs mounts?

| Type | Description |
|---|---|
| Volume | Managed by Docker |
| Bind Mount | Uses host directory |
| tmpfs | Stored in memory only |

---

# 16. 🌐 How does Docker networking work?

- Docker creates networks for containers to communicate.
- Containers inside same network can talk using container names.


# 17. 🔌 What are bridge, host, and overlay networks?

| Network Type | Description |
|---|---|
| Bridge | Default network for containers |
| Host | Uses host machine network |
| Overlay | Connects containers across multiple hosts |

---

# 18. 🔗 How do containers communicate with each other?

- Containers communicate using:
 - ✅ Container names
 - ✅ IP addresses
 - ✅ Shared Docker network  

### 📌 Example:

- Java app connects to MySQL using:

```text
mysql-container:3306
```

---

# 19. 🌍 How does port mapping work in Docker?

- Port mapping exposes container port to host machine.

### 📌 Example:

```bash
docker run -p 8080:80 nginx
```

- Meaning:
   - ✅ Host port = 8080
   - ✅ Container port = 80  

---

# 20. 📘 What is Docker Compose and why is it used?

- Docker Compose manages multi-container applications using YAML file.
- Used for:
  - ✅ Running app + database together
  - ✅ Easier setup  

---

# 21. 🧱 How do you define multi-container applications using Docker Compose?

### 📌 Example:

```yaml
version: '3'

services:
  app:
    image: myapp

  mysql:
    image: mysql
```

---

# 22. 🔐 How do environment variables and secrets work in Docker?

- Environment variables store configuration values.

### 📌 Example:

```bash
docker run -e DB_USER=root myapp
```
- Secrets securely store sensitive data like passwords.

---

# 23. 💽 How do you persist database data in containers?

- Use Docker volumes.
- Data remains even if container stops.

### 📌 Example:

```bash
docker run -v dbdata:/var/lib/mysql mysql
```

---

# 24. 📊 What are stateless vs stateful containers?

| Stateless | Stateful |
|---|---|
| No stored data | Stores data |
| Easy to scale | Needs persistent storage |

### 📌 Example:

- ✅ Stateless = Java REST API  
- ✅ Stateful = MySQL database  

---

# 25. 🐞 How do you debug a failing Docker container?

- ✅ Check logs
- ✅ Inspect container
- ✅ Enter container shell
- ✅ Verify ports and environment variables  

---

# 26. 📈 How do you inspect logs and container metrics?

## 🔹 Logs :

```bash
docker logs container_id
```

## 🔹 Metrics:

```bash
docker stats
```

---

# 27. 🖥️ How do you access a running container for troubleshooting?

```bash
docker exec -it container_id bash
```

---

# 28. ❤️ How do health checks work in Docker?

- Health checks monitor container status.

### 📌 Example:

- Docker checks if Java application endpoint is responding.

## 📍 States:

- ✅ healthy
- ✅ unhealthy  

---

# 29. 💥 What happens when a container crashes?

- ✅ Container stops
- ✅ Logs are generated
- ✅ Restart policy may restart it automatically  

---

# 30. 🔁 How do restart policies work in Docker?

- Restart policies define container restart behavior.

example:

```bash
--restart always
--restart on-failure
```

---

# 31. 🛡️ How do you secure Docker containers?

- ✅ Use trusted images
- ✅ Avoid root user
- ✅ Scan vulnerabilities
- ✅ Limit permissions
- ✅ Keep images updated  

---

# 32. 🔒 What are Docker security best practices?

- ✅ Use minimal images
- ✅ Avoid hardcoded secrets
- ✅ Use read-only filesystem
- ✅ Scan images regularly
- ✅ Limit container privileges  

---

# 33. 👤 Why should containers avoid running as root?

- Running as root increases security risk.
- If container is hacked, attacker may get high system access.

## ✅ Best practice:

- Create non-root user.

### 📌 Example:

```dockerfile
USER appuser
```

---

# 34. 🔍 How do you scan Docker images for vulnerabilities?

- Use tools like:
   - ✅ Docker Scout
   - ✅ Trivy
   - ✅ Snyk  

---

# 35. ⚡ What are common Docker performance optimization techniques?

- ✅ Use smaller images  
- ✅ Reduce layers
- ✅ Use caching
- ✅ Use multi-stage builds
- ✅ Limit container resources
- ✅ Remove unused containers/images  

---

# 🧊 What is a Distroless Image?

- A distroless image is a minimal Docker image that contains only:
  - ✅ Application
  - ✅ Required runtime libraries  
- It does NOT contain:
  - ❌ Shell (bash, sh)
  - ❌ Package managers
  - ❌ Debugging tools  

## 🎯 Purpose:

- ✅ Smaller image size  
- ✅ Better security  
- ✅ Faster startup  

### 📌 Example:

For Java app:

```dockerfile
FROM gcr.io/distroless/java17
COPY app.jar app.jar
CMD ["app.jar"]
```

---

# ⚖️ Difference Between Multi-Stage Build and Distroless Image

| Multi-Stage Build | Distroless Image |
|---|---|
| Docker build technique | Minimal runtime image |
| Uses multiple FROM stages | Uses lightweight secure base image |
| Reduces unnecessary build files | Removes OS tools and utilities |
| Helps reduce image size | Helps improve security |
| Can use any base image | Uses special distroless images |

---

# 📌 Example

## 🔹 Multi-Stage Build

```dockerfile
FROM maven:3.9-eclipse-temurin-17 AS build
COPY . .
RUN mvn clean package

FROM openjdk:17-jdk-slim
COPY --from=build target/app.jar app.jar
CMD ["java", "-jar", "app.jar"]
```

- Here:
  - ✅ First stage builds app   
  - ✅ Second stage runs app  

---

## 🔹 Distroless Example

```dockerfile
FROM maven:3.9-eclipse-temurin-17 AS build
COPY . .
RUN mvn clean package

FROM gcr.io/distroless/java17
COPY --from=build target/app.jar app.jar
CMD ["app.jar"]
```

- Here:
  - ✅ Final image is distroless
  - ✅ No shell or package manager exists  

---

# ✅ Advantages of Multi-Stage Build

- ✅ Smaller image size
- ✅ Cleaner production image
- ✅ Removes build tools from final image
- ✅ Better performance  

---

# ❌ Disadvantages of Multi-Stage Build

- ❌ Dockerfile becomes bigger
- ❌ Slightly harder to understand for beginners  

---

# ✅ Advantages of Distroless Image

- ✅ Very small image
- ✅ Better security
- ✅ Fewer vulnerabilities
- ✅ Faster deployment  

---

# ❌ Disadvantages of Distroless Image

- ❌ No shell access
- ❌ Difficult debugging
- ❌ Cannot install tools inside container
- ❌ Troubleshooting becomes harder  

---
