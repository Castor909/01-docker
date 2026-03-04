# Docker Assignment: Complete Guide (English Version)

## Part A: Docker Fundamentals

### Task 1: Docker Installation and Non-Privileged User Setup

#### Required Actions:
1. **Install Docker** on your Linux machine
2. **Configure Docker** to work without root privileges

#### Commands:

**Debian/Ubuntu:**
```bash
# Install Docker
sudo apt-get update
sudo apt-get install docker.io -y

# Add your user to the docker group
sudo usermod -aG docker $USER
newgrp docker

# Verify installation
docker --version
docker run hello-world
```

**Arch Linux / CachyOS / Manjaro:**
```bash
# Install Docker
sudo pacman -Syu
sudo pacman -S docker

# Add your user to the docker group
sudo usermod -aG docker $USER
newgrp docker

# Start and enable Docker service
sudo systemctl start docker
sudo systemctl enable docker

# Verify installation
docker --version
docker run hello-world
```

**What to document:** Screenshot showing `docker --version` and successful `hello-world` output without using `sudo`.

---

### Task 2: Hello-World Container Lifecycle

#### Required Actions:
1. Run hello-world container
2. Verify the output
3. Check that it's not running
4. List stopped containers
5. Delete the container

#### Commands:
```bash
# Run hello-world container
docker run hello-world

# List all containers (including stopped ones)
docker ps -a

# Get container ID from the output above, then delete it
docker rm <CONTAINER_ID>

# Verify deletion
docker ps -a
```

**What to document:** 
- Screenshot of successful `hello-world` output
- Screenshot of `docker ps -a` showing the container
- Screenshot of `docker ps -a` showing the container has been deleted

---

### Task 3: Interactive Debian Container with Package Installation

#### Required Actions:
1. Create interactive Debian container
2. Install `nano` package
3. Exit and verify it's not running
4. Restart and check if `nano` persists
5. Delete container
6. Create new Debian container and verify `nano` is not installed

#### Commands:
```bash
# Create interactive Debian container
docker run -it debian /bin/bash

# Inside the container, run:
apt-get update
apt-get install nano -y
nano  # Test that it works
exit  # Exit the container

# List containers
docker ps -a

# Restart the container (use the container ID or name)
docker start <CONTAINER_ID>
docker attach <CONTAINER_ID>

# Inside: verify nano is still there
which nano
exit

# Delete the container
docker rm <CONTAINER_ID>

# Create a new Debian container
docker run -it debian /bin/bash

# Inside: verify nano is NOT installed
which nano  # Should show: nano not found
exit

# Clean up
docker ps -a
docker rm <CONTAINER_ID>
```

**What to document:**
- Screenshot of `nano` installation
- Screenshot showing `nano` is installed after restart
- Screenshot showing `nano` is NOT installed in new container
- Screenshot showing container lifecycle (`docker ps -a` at different stages)

---

### Task 4: Nginx Daemon Container

#### Required Actions:
1. Create daemon container from official nginx image
2. No additional command needed (nginx starts automatically)
3. Access via web browser
4. View container logs

#### Commands:
```bash
# Create and run nginx daemon container
docker run -d --name my_nginx nginx

# List running containers
docker ps

# Get the IP address of the Docker host
hostname -I
# or
ip addr show

# View logs
docker logs my_nginx

# Access via browser: http://<DOCKER_HOST_IP>:80
# Note: Since it's a daemon, the container stays running even after the command returns
```

**What to document:**
- Screenshot of `docker run -d --name my_nginx nginx` command
- Screenshot of `docker ps` showing the running container
- Screenshot of web browser accessing nginx (http://localhost or http://<DOCKER_IP>)
- Screenshot of `docker logs my_nginx` output

---

### Task 5: NextCloud Container with SQLite Configuration

#### Required Actions:
1. Create NextCloud container
2. Configure custom SQLite database name
3. Verify it's running

#### Commands:
```bash
# Create NextCloud container with custom database name
# Reference: https://hub.docker.com/_/nextcloud
docker run -d \
  --name nextcloud \
  -p 8080:80 \
  -e SQLITE_DB=mydb \
  nextcloud

# Wait for the container to start (may take 30-60 seconds)
sleep 60

# Check if container is running
docker ps

# View logs
docker logs nextcloud

# Access via browser
# Open: http://localhost:8080 or http://<DOCKER_IP>:8080
```

**Note:** You may need to configure NextCloud through the web interface. Default setup through web installer.

**What to document:**
- Screenshot of `docker run` command execution
- Screenshot of `docker ps` showing the running NextCloud container
- Screenshot of NextCloud web interface (http://localhost:8080)
- Screenshot of `docker logs nextcloud` showing startup messages

---

## Part B: Nginx Container on Custom Port

### Requirement:
Create daemon nginx container:
- Name: `servidor_web`
- Port mapping: 8181 (host) → 80 (container)
- Run in background
- Access via `http://localhost:8181`

#### Commands:
```bash
# Create and run nginx container
docker run -d \
  --name servidor_web \
  -p 8181:80 \
  nginx

# Verify it's running
docker ps

# Access via browser: http://localhost:8181
# If testing from another machine use: http://<DOCKER_HOST_IP>:8181
```

### Task 1: Container Creation and Verification

#### Commands:
```bash
# Run the container
docker run -d --name servidor_web -p 8181:80 nginx

# Verify container is running
docker ps

# Check container details
docker inspect servidor_web
```

**What to document:** Screenshot showing container creation and `docker ps` output.

---

### Task 2: Web Browser Access

#### Required:
Access the nginx server via web browser on port 8181

#### Steps:
1. Open web browser
2. Navigate to `http://localhost:8181`
3. You should see the default nginx welcome page

**What to document:** Screenshot of the nginx welcome page in your browser showing the address bar with port 8181.

---

### Task 3: Local Images Registry

#### Commands:
```bash
# List all local images
docker images

# Get more details
docker images -a
```

**What to document:** Screenshot of `docker images` output showing all your local images.

---

### Task 4: Container Deletion

#### Commands:
```bash
# First, stop the container
docker stop servidor_web

# Verify it's stopped
docker ps -a | grep servidor_web

# Delete the container
docker rm servidor_web

# Verify deletion
docker ps -a | grep servidor_web  # Should show nothing
```

**What to document:** Screenshot showing:
1. `docker stop servidor_web`
2. `docker ps -a` with stopped container
3. `docker rm servidor_web`
4. `docker ps -a` showing container is gone

---

## Summary: What You Need to Do

1. **Execute all Docker commands** on your machine
2. **Take screenshots** of each step as indicated
3. **Document results** in the repository
4. **Submit before deadline:** October 23, 23:59

### Cleanup Commands (when done):
```bash
# Remove all stopped containers
docker container prune

# List remaining containers
docker ps -a

# Remove images if needed
docker rmi <IMAGE_ID>
```

---

## Tips

- Use `docker ps -a` to see all containers (running and stopped)
- Use `docker logs <CONTAINER_NAME>` to debug issues
- Use `docker exec -it <CONTAINER_NAME> bash` to enter a running container
- Port mapping format: `-p HOST_PORT:CONTAINER_PORT`
- Container names must be unique
- Remove containers before creating with the same name: `docker rm <NAME>`

