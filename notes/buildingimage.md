# Containerizing a Web Application

## Objective

The objective of this practical was to create a simple web server application, build a Docker image for it, run the image as a container, and push the image to Docker Hub.

---

## Tasks Performed

### Task 1: Start Web Server

A local project folder was created for the application.

```bash
mkdir -p ~/myapp
cd ~/myapp
```

A Python application file (`app.py`) was created inside the folder and tested locally.

```bash
python3 app.py
```

A `Dockerfile` was then created inside the project folder.

```bash
nano Dockerfile
```

The Docker image was built and run as a container.

```bash
docker build -t flaskapp .
docker run -p 8080:8080 flaskapp
```

> The `-p 8080:8080` flag maps port 8080 on the container to port 8080 on the host machine, making the app accessible at `http://localhost:8080`.

---

### Task 2: Push Image to Docker Hub

The image was tagged with the Docker Hub username and image name.

```bash
docker build . -t ash5zero3/<image_name>
```

The tagged image was then pushed to Docker Hub.

```bash
docker push ash5zero3/<image_name>
```

> Replace `<image_name>` with the actual name of your image (e.g., `flaskapp`).

---

## Learning Outcome

From this practical, I learned how to containerize a simple application using Docker. I also learned how to:

- Write a `Dockerfile` to define how the image should be built
- Build a Docker image locally using `docker build`
- Run the image as a container and expose it on a port
- Tag the image properly with a Docker Hub username
- Push the image to Docker Hub so it can be shared and run on other machines

---

## Quick Reference

| Command | Description |
|---|---|
| `docker build -t <name> .` | Build an image from the current directory |
| `docker run -p 8080:8080 <name>` | Run a container and map ports |
| `docker build . -t username/<name>` | Build and tag for Docker Hub |
| `docker push username/<name>` | Push image to Docker Hub |
