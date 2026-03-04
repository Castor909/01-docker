# Part A: Docker Fundamentals

## Task 1: Docker Installation and Non-Privileged User Setup

**Status:** ❌ Not completed

### Required screenshots:
- [ ] Output of `docker --version` without using `sudo`
- [ ] Successful run of `docker run hello-world`

### Commands to execute:

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

### Notes:
- If the newgrp command doesn't work, log out and log back in
- Verify that `docker run` works WITHOUT `sudo`
- For CachyOS use commands as for Arch Linux

---

## Task 2: Hello-World Container Lifecycle

**Status:** ❌ Not completed

### Required screenshots:
- [ ] Output of `docker run hello-world`
- [ ] Output of `docker ps -a` with container listed
- [ ] Output of `docker ps -a` after deleting container

### Commands to execute:
```bash
# Run container
docker run hello-world

# List all containers (including stopped ones)
docker ps -a

# Delete container by ID or name
docker rm <CONTAINER_ID>

# Verify deletion
docker ps -a
```

---

## Task 3: Interactive Debian Container with Package Installation

**Status:** ❌ Not completed

### Required screenshots:
- [ ] Installation of `nano` in container
- [ ] `nano` installed after container restart
- [ ] In new container `nano` is NOT installed
- [ ] Container lifecycle (`docker ps -a` at different stages)

### Commands to execute:
```bash
# Create interactive Debian container
docker run -it debian /bin/bash

# Inside container, run:
apt-get update
apt-get install nano -y
nano  # Test that it works
exit  # Exit container

# List containers
docker ps -a

# Restart container (use container ID or name)
docker start <CONTAINER_ID>
docker attach <CONTAINER_ID>

# Inside: verify nano is still there
which nano
exit

# Delete container
docker rm <CONTAINER_ID>

# Create new Debian container
docker run -it debian /bin/bash

# Inside: verify nano is NOT installed
which nano  # Should show: nano not found
exit

# Clean up
docker ps -a
docker rm <CONTAINER_ID>
```

---

## Task 4: Nginx Daemon Container

**Status:** ❌ Not completed

### Required screenshots:
- [ ] Command `docker run -d --name my_nginx nginx`
- [ ] Output of `docker ps` with running container
- [ ] Browser window accessing nginx (http://localhost)
- [ ] Output of `docker logs my_nginx`

### Commands to execute:
```bash
# Create and run nginx daemon container
docker run -d --name my_nginx nginx

# List running containers
docker ps

# Get the IP address of Docker host
hostname -I
# or
ip addr show

# View logs
docker logs my_nginx

# Access via browser: http://localhost or http://<DOCKER_IP>
# Note: Since it's a daemon, the container stays running even after the command returns
```

---

## Task 5: NextCloud Container with SQLite Configuration

**Status:** ❌ Not completed

### Required screenshots:
- [ ] Container creation command
- [ ] Output of `docker ps` with running NextCloud
- [ ] Browser window with NextCloud interface (http://localhost:8080)
- [ ] Output of `docker logs nextcloud`

### Commands to execute:
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

### Notes:
- NextCloud will be accessible through the web interface
- You may need to configure NextCloud through the web installer
- Wait several minutes for full loading

---

## Summary

Complete all 5 tasks in order. Take screenshots of each step as indicated. Save screenshots in the [screenshots/](screenshots/) folder.

For quick command reference, see [CHEATSHEET_EN.md](../CHEATSHEET_EN.md)
