### 1. docker exec vs docker attach
- docker exec starts a brand-new process inside an already running container (such as opening a fresh bash shell). If you exit that shell, only the new process stops—your main container keeps running uninterrupted.
- docker attach connects your terminal directly to the container's existing main process (PID 1). Because you are plugged straight into the main process, pressing Ctrl+C or typing exit will stop the entire container unless you use the special detach key sequence (Ctrl+P followed by Ctrl+Q).


### 2. docker run vs docker exec
- docker run creates and starts a completely new container from an image. You use this when launching an application for the first time.
- docker exec runs a command inside a container that is already created and running. You cannot use docker exec on a stopped container or directly on an image.


### 3. Why do we use docker logs?
- Containers typically run in the background (detached mode) without a visible screen or terminal window. 
- docker logs fetches everything the container's main process has printed to standard output (stdout) and standard error (stderr), making it the primary tool for checking startup status, diagnosing crashes, and monitoring application errors without entering the container.


### 4. What information does docker inspect provide?
docker inspect outputs a detailed JSON report containing the complete low-level configuration and runtime state of a Docker object (container, image, volume, or network). Key details include:
- Network settings: Internal IP addresses, port mappings, and connected networks.
- Storage: Mounted volumes and bind mount paths.
- State & Lifecycle: Current status, start/finish timestamps, restart count, and exit code.
- Configuration: Environment variables, startup commands (ENTRYPOINT/CMD), and resource limits.


### 5. Difference between docker stats and docker top
- docker stats shows a live, real-time stream of resource consumption—specifically CPU percentage, memory usage, network I/O, and disk read/write rates—across one or more containers.
- docker top displays a static snapshot of the active processes running inside a specific container (similar to running ps aux on Linux), showing process IDs (PIDs), owners, and the exact commands executing.


### 6. What is an exit code?
An exit code is a numeric status returned by a container's main process when it stops, telling you why it terminated:
- 0: Clean, intentional exit with no errors.
- 1 (or other non-zero numbers): The application encountered an error or crashed.
- 137: The container was forcefully killed (SIGKILL), often because it ran out of memory (OOM) or was stopped with docker kill.
- 143: The container received a graceful termination signal (SIGTERM), usually triggered by docker stop.


### 7. Why is docker exec -it useful for debugging?
- Combining -i (interactive, keeps STDIN open) and -t (allocates a pseudo-TTY) gives you a full, interactive command-line session inside a running container. 
- This allows you to inspect config files, verify environment variables, test network connectivity (e.g., curl or ping), and check file permissions live without modifying your image or restarting the service.