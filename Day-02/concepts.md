# Essential Docker Concepts Explained

#### 1. Detached Mode vs. Interactive Mode
Think of this as running an app in the background versus working directly inside a terminal window.
* **Detached Mode (`-d`):** The container runs silently in the background. You start it, Docker hands you back your terminal prompt immediately, and the container keeps doing its job (like hosting a web server) while you move on to other tasks.
* **Interactive Mode (`-it`):** You are stepped *inside* the container. Your terminal is connected directly to the container's shell, allowing you to type commands, explore files, and see live output directly on your screen—just like using SSH to log into another computer.


#### 2. `docker run` vs. `docker start`
The main difference here is **creating something new** versus **waking up something that already exists**.
* **`docker run`:** Builds a brand-new container from an image blueprint and immediately boots it up. Every time you use `docker run`, you get a fresh, separate container instance.
* **`docker start`:** Takes a container that you *already created* earlier (which is currently stopped) and turns it back on, preserving any changes or files saved inside that specific container's writable layer.


#### 3. `docker stop` vs. `docker pause`
- Both commands halt what a container is doing, but they handle the container's memory and processes very differently.
* **`docker stop`:** Shuts the container down cleanly. It sends a polite signal (`SIGTERM`) asking the application inside to finish what it's doing, save its state, and exit. Once stopped, the container uses **zero CPU and zero RAM**.
* **`docker pause`:** Freezes the container in time. It doesn't shut anything down; it simply suspends all running processes in place. The container uses **zero CPU**, but everything remains sitting in **RAM**, ready to resume instantly the exact microsecond you unpause it.


#### 4. `docker rm` vs. `docker rm -f`
This comes down to safety checks versus brute force when deleting containers.
* **`docker rm`:** The safe delete. Docker checks if the container is stopped first. If it's still running, Docker refuses to delete it and gives you an error so you don't accidentally wipe out live work.
* **`docker rm -f`:** The force delete. It skips the safety check, immediately kills the running process (`SIGKILL`) without giving it time to clean up or save data, and deletes the container on the spot.


#### 5. What happens when you exit an interactive container?
- When you type `exit` (or press `Ctrl + D`) inside an interactive container, **the container stops running**. 
- A Docker container only stays alive as long as its main foreground process (usually the shell, like `/bin/bash`) is running. 
- When you exit the shell, that main process ends, so Docker shuts the container down. 
- However, **it is not deleted**—it simply moves to an `Exited` state, and you can bring it back anytime with `docker start`. 


#### 6. What happens to an image when its container is deleted?
- Think of a Docker image as a **cookie cutter** (or a read-only blueprint) and a container as the **cookie**. 
- Throwing away a cookie doesn't destroy the cookie cutter; your image stays safely stored on your machine so you can spin up new containers from it whenever you want.
- Images are only removed if you explicitly delete them using `docker rmi`.