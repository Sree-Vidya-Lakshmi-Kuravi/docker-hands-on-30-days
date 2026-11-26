
# Day 1 - Docker Commands

## 1. Check Docker version
```bash
docker --version
```
Purpose: Displays the installed Docker version.

## 2. Docker information
```bash
docker info
```
Purpose: Displays Docker Engine information.

## 3. Check Docker service
```bash
sudo systemctl status docker
```
Purpose: Checks whether Docker service is running.

## 4. Run Hello World
```bash
docker run hello-world
```
Purpose: Pulls the image if needed, creates and runs a container.

## 5. List images
```bash
docker images
```
Purpose: Displays locally available images.

## 6. List running containers
```bash
docker ps
```

## 7. List all containers
```bash
docker ps -a
```

## 8. List container IDs
```bash
docker ps -aq
```

## 9. List image IDs
```bash
docker images -q
```
  