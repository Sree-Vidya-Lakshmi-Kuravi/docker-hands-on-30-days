### 1. What is a container?
- A container is an isolated section of an operating system that is dedicated to running one application and its dependencies.
- Most popular way to package and run modern applications.


### 2. What is docker?
- Docker is an open-source platform that packages applications and all their dependencies into standardized, isolated units called containers. 
- It solves the classic "it works on my machine" problem by ensuring software runs identically across a developer's laptop, a testing server, or the cloud.


### 3. What is containerization?
- The process of packaging an application as an image is called *containerization.*
- It takes the application source code, including all the dependencies and builds it into an image.
- This image is usually small and contains everything needed to run the app.
- One you have the *image*, you can run it as a *container*.


### 4. What is a Docker image?
- An image is a collection of *layers* that comprise the application and all dependencies.
- A Docker image is like a snapshot of an app and everything it needs to run.


### 5. What is Docker Hub?
- Docker Hub is the official cloud-based container registry and software artifact distribution platform maintained by Docker for storing, sharing, and managing container images. 
- It acts as the default registry where Docker looks for images when you build or run containers.


### 6. Containers vs Virtual Machines
- A VM virtualizes **hardware**, so each VM gets its **own complete operating system (kernel + OS files)**.
- A container virtualizes the **OS layer**, so containers **share the host OS kernel** and only package the app and its dependencies.


### 7. Images vs Containers
- **Docker Image**: An immutable package containing an application, runtime, libraries, and dependencies.
- **Docker Container**: A running, isolated instance of a Docker image.