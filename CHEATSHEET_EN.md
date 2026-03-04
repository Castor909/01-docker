# 🚀 Docker Cheatsheet - Most Important Commands

## Part A - Task 1: Install Docker

**Debian/Ubuntu:**
```bash
# Installation
sudo apt-get update && sudo apt-get install docker.io -y

# Add to docker group
sudo usermod -aG docker $USER && newgrp docker

# Verification
docker --version && docker run hello-world
```

**Arch Linux / CachyOS / Manjaro:**
```bash
# Installation
sudo pacman -Syu && sudo pacman -S docker

# Add to docker group
sudo usermod -aG docker $USER && newgrp docker

# Start service
sudo systemctl start docker && sudo systemctl enable docker

# Verification
docker --version && docker run hello-world
```

---

## Part A - Task 2: Hello-World container

```bash
# Run container
docker run hello-world

# List containers
docker ps -a

# Delete container (replace <ID> with your ID from docker ps -a)
docker rm <ID>
```

---

## Part A - Task 3: Debian + nano

### Create container and install nano
```bash
docker run -it debian /bin/bash
# Inside container run:
apt-get update && apt-get install nano -y
nano
exit
```

### Check that container exists and restart
```bash
# List with ID
docker ps -a

# Restart container (replace <ID> with your ID)
docker start <ID>
docker attach <ID>
# Check that nano is still there
which nano
exit
```

### Delete old and create new container
```bash
# Delete old container
docker rm <ID>

# Create new Debian container
docker run -it debian /bin/bash
# Check that nano is NOT installed
which nano
exit
```

---

## Part A - Task 4: Nginx daemon

```bash
# Create and run
docker run -d --name my_nginx nginx

# Check status
docker ps

# Get IP address for browser
hostname -I

# View logs
docker logs my_nginx

# Browser access: http://localhost (default port 80)
```

---

## Part A - Task 5: NextCloud

```bash
# Create container
docker run -d \
  --name nextcloud \
  -p 8080:80 \
  -e SQLITE_DB=mydb \
  nextcloud

# Wait for loading
sleep 60

# Check
docker ps

# View logs (wait until ready)
docker logs nextcloud

# Browser access: http://localhost:8080
```

---

## Part B: Nginx on port 8181

### Task 1: Create container
```bash
# Create
docker run -d --name servidor_web -p 8181:80 nginx

# Check
docker ps
docker inspect servidor_web
```

### Task 2: Web access
```bash
# Browser → http://localhost:8181
# Or use IP address:
firefox http://$(hostname -I | awk '{print $1}'):8181
```

### Task 3: List images
```bash
docker images
```

### Task 4: Delete container
```bash
# Stop
docker stop servidor_web

# Check it's stopped
docker ps -a | grep servidor_web

# Delete
docker rm servidor_web

# Check it's deleted
docker ps -a | grep servidor_web
```

---

## ⚡ First Aid Commands

### If container won't start
```bash
# Check logs
docker logs <NAME>

# Delete and recreate
docker rm -f <NAME>
```

### If Docker requires sudo
```bash
# Check group
groups $USER

# Add to group
sudo usermod -aG docker $USER && newgrp docker
```

### If you need to clean up system
```bash
# Delete stopped containers
docker container prune

# Delete unused images
docker image prune

# Clean everything
docker system prune -a
```

---

## 📋 Getting container or image ID

```bash
# Output with single column (ID only)
docker ps -aq              # all containers
docker ps -q               # running containers
docker images -q           # all images

# Example usage
CONTAINER_ID=$(docker ps -aq | head -1)
docker rm $CONTAINER_ID
```

---

## 🎯 Checklist before submission

### Part A:
- [ ] Task 1: Docker installed, works without sudo
- [ ] Task 2: Hello-world ran and deleted
- [ ] Task 3: Debian container with nano, verified it doesn't copy to new one
- [ ] Task 4: Nginx works, accessible in browser
- [ ] Task 5: NextCloud works, accessible in browser

### Part B:
- [ ] Task 1: Container `servidor_web` created and running
- [ ] Task 2: Accessible at http://localhost:8181
- [ ] Task 3: `docker images` shows all images
- [ ] Task 4: Container stopped and deleted

### Documentation:
- [ ] All screenshots saved in correct folders
- [ ] Each screenshot is labeled and clear
- [ ] Repository updated (git push)

---

## 📚 Useful links

- [Docker Documentation](https://docs.docker.com/)
- [Docker Hub - find images](https://hub.docker.com/)
- [Nginx image](https://hub.docker.com/_/nginx)
- [Debian image](https://hub.docker.com/_/debian)
- [NextCloud image](https://hub.docker.com/_/nextcloud)

---

**Remember:** If something isn't clear - check [DOCKER_COMMANDS_REFERENCE.md](DOCKER_COMMANDS_REFERENCE.md) for full reference!
