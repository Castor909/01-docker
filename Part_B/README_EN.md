# Part B: Nginx Container on Custom Port

**Main requirements:**
- Container name: `servidor_web`
- Host port: 8181
- Container port: 80
- Image: nginx

---

## Task 1: Create Container and Verify Status

**Status:** ❌ Not completed

### Required screenshots:
- [ ] Container creation command with output
- [ ] Output of `docker ps` confirming container is running

### Commands to execute:
```bash
# Create and run nginx container
docker run -d \
  --name servidor_web \
  -p 8181:80 \
  nginx

# Verify that container is running
docker ps

# Additional information about container
docker inspect servidor_web
```

### Expected result:
- Container `servidor_web` is running
- Port 8181 is forwarded to port 80 of the container

---

## Task 2: Access via Web Browser

**Status:** ❌ Not completed

### Required screenshots:
- [ ] Browser window with address http://localhost:8181 or http://<IP>:8181
- [ ] Visible nginx welcome page (Welcome to nginx!)

### How to verify:
1. Open web browser
2. Navigate to `http://localhost:8181`
3. If browser is on different machine, use Docker host IP address
4. After successful connection, take screenshot

### Getting IP address:
```bash
# IP address of your Docker host
hostname -I
```

---

## Task 3: List Local Images

**Status:** ❌ Not completed

### Required screenshots:
- [ ] Output of `docker images` with all your local images

### Commands to execute:
```bash
# List all images
docker images

# More detailed list
docker images -a

# Image sizes
docker images --no-trunc
```

### Expected result:
You will see images:
- `nginx`
- `debian` (if you completed Part A tasks)
- `nextcloud` (if you completed Part A tasks)
- `hello-world` (if you completed Part A tasks)

---

## Task 4: Delete Container

**Status:** ❌ Not completed

### Required screenshots:
- [ ] Command `docker stop servidor_web`
- [ ] Output of `docker ps -a` with stopped container
- [ ] Command `docker rm servidor_web`
- [ ] Output of `docker ps -a` confirming container deletion

### Commands to execute:
```bash
# 1. Stop the container
docker stop servidor_web

# 2. Verify it's stopped
docker ps -a | grep servidor_web

# 3. Delete the container
docker rm servidor_web

# 4. Verify it's deleted
docker ps -a | grep servidor_web  # Should show nothing
```

### Notes:
- IMPORTANT: Container MUST be stopped before deletion
- If not - use `docker rm -f servidor_web` (force deletion)

---

## Additional Commands for Working

```bash
# View container logs
docker logs servidor_web

# Stop without deleting
docker stop servidor_web

# Restart container
docker start servidor_web

# Enter running container
docker exec -it servidor_web bash

# Container information
docker inspect servidor_web

# Container statistics
docker stats servidor_web
```

---

## Summary

Complete all 4 tasks in order. Take screenshots of each step as indicated. Save screenshots in the [screenshots/](screenshots/) folder.

For quick command reference, see [CHEATSHEET_EN.md](../CHEATSHEET_EN.md)
