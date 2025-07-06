# Bootcamp Java MySQL Project

**This project is for personal training purposes only as part of DevOps training for Techworld with Nana.**
**It is not for redistribution or commercial use. All rights reserved.**

A full-stack Java Spring Boot application with MySQL, packaged for easy Docker deployment. The app features a modern UI for managing team member roles, with avatars and edit functionality.

![App Screenshot](images/screenshot.png)

---

## Project Structure

```
bootcamp-java-mysql-project/
├── build.gradle                # Gradle build file
├── Dockerfile                  # Docker build file for Java app
├── docker-compose.yaml         # Docker Compose for multi-container setup
├── src/
│   └── main/
│       └── resources/
│           └── static/
│               └── index.html # Main frontend file
├── build/
│   └── libs/
│       └── bootcamp-java-mysql-project-1.0-SNAPSHOT.jar # Built JAR
└── ...
```

---

## Prerequisites
- Java 8+
- Gradle (or use the included wrapper)
- Docker & Docker Hub account

---

## Step-by-Step Instructions

### 1. Edit Static Files (Frontend)
Edit your UI in:
```
src/main/resources/static/index.html
```

### 2. Build the JAR (Backend)
From the project root:
```sh
./gradlew build
```
This creates:
```
build/libs/bootcamp-java-mysql-project-1.0-SNAPSHOT.jar
```

### 3. Build the Docker Image
```sh
docker build --no-cache -t <your-dockerhub-username>/java-image-2.0:latest .
```

### 4. Push the Image to Docker Hub
```sh
docker push <your-dockerhub-username>/java-image-2.0:latest
```

### 5. (Optional) Run Locally with Docker Compose
You can use the provided `docker-compose.yaml` to run the app, MySQL, and phpMyAdmin locally:
```sh
docker-compose up -d
```

---

## Deployment Note
Once your image is built and pushed to Docker Hub, you can use deployment tools (such as Ansible, in a separate project) to:
- Pull the image onto a remote server (e.g., EC2)
- Launch the app using your `docker-compose.yaml`

Example (on your server):
```sh
docker pull <your-dockerhub-username>/java-image-2.0:latest
docker-compose up -d
```

---

## Troubleshooting
- Always rebuild the JAR after editing static files.
- Always build and push the Docker image after changes.
- Use `--no-cache` with `docker build` to avoid stale builds.
- Check the running container for the latest static files if changes are not visible.

---

## License
MIT
