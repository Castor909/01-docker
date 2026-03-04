# Instructions: How to Complete the Assignment

## 📋 Quick action plan

### Part A - 5 main tasks
1. ✅ Install Docker and configure non-privileged user
2. ✅ Hello-World container
3. ✅ Debian container with nano
4. ✅ Nginx daemon container
5. ✅ NextCloud with SQLite

### Part B - Nginx on port 8181
1. ✅ Create `servidor_web` container
2. ✅ Access via web browser
3. ✅ List local images
4. ✅ Delete container

---

## 🚀 Quick Start

### Step 1: Getting Familiar (5-10 minutes)
1. Read [Part_A/README_EN.md](Part_A/README_EN.md) - description of all tasks
2. Read [Part_B/README_EN.md](Part_B/README_EN.md) - description of Part B tasks
3. Use [DOCKER_COMMANDS_REFERENCE.md](DOCKER_COMMANDS_REFERENCE.md) as needed - command reference

### Step 2: Complete Tasks
**Navigate through files:**
- For **Part A**: open [Part_A/README_EN.md](Part_A/README_EN.md)
- For **Part B**: open [Part_B/README_EN.md](Part_B/README_EN.md)

### Step 3: Documentation
1. Execute commands from the files
2. Take screenshots as indicated
3. Save screenshots in corresponding folders:
   - Part A screenshots → `Part_A/screenshots/`
   - Part B screenshots → `Part_B/screenshots/`

### Step 4: Commit and Push
```bash
# Add all files to git
git add .

# Create commit
git commit -m "Part A and B: Docker assignment completed with screenshots"

# Push to server
git push origin main
```

---

## 📸 Where to save screenshots

**Folder structure:**
```
01-docker/
├── Part_A/
│   ├── README_EN.md
│   └── screenshots/
│       ├── task_1_docker_version.png
│       ├── task_1_hello_world.png
│       ├── task_2_docker_run.png
│       ├── task_2_ps_with_container.png
│       ├── task_2_ps_after_deletion.png
│       ├── task_3_nano_install.png
│       ├── task_3_nano_after_restart.png
│       ├── task_3_nano_not_installed.png
│       ├── task_3_ps_lifecycle.png
│       ├── task_4_nginx_run.png
│       ├── task_4_ps_running.png
│       ├── task_4_browser_access.png
│       ├── task_4_logs.png
│       ├── task_5_nextcloud_run.png
│       ├── task_5_ps_running.png
│       ├── task_5_browser_access.png
│       └── task_5_logs.png
└── Part_B/
    ├── README_EN.md
    └── screenshots/
        ├── task_1_create_container.png
        ├── task_1_ps_running.png
        ├── task_2_browser_port_8181.png
        ├── task_3_docker_images.png
        ├── task_4_stop_container.png
        ├── task_4_ps_stopped.png
        ├── task_4_rm_container.png
        └── task_4_ps_deleted.png
```

---

## ⏰ Deadlines

**Deadline:** October 23, 23:59

**Recommended schedule:**
- **Day 1-2:** Part A tasks 1-2 (installation and basic commands)
- **Day 3-4:** Part A tasks 3-4 (containers and daemon)
- **Day 5:** Part A task 5 (NextCloud)
- **Day 6-7:** Part B (remote work)
- **Day 8:** Finalization and commit

---

## 💡 Useful tips

### Before you start
- ✅ Make sure Docker is installed
- ✅ Check internet connection (to download images)
- ✅ Have a browser ready (to test services)
- ✅ Make sure you have ~2 GB free disk space

### During execution
- 📍 Read requirements for each task carefully
- 📍 Copy commands completely (including flags)
- 📍 Wait for full container loading (especially NextCloud)
- 📍 If error occurs - check logs: `docker logs <NAME>`

### With screenshots
- 📸 Include address bar in browser (to show http://localhost:...)
- 📸 Show full command output (without truncation)
- 📸 One action = one screenshot
- 📸 Use OS screenshot tool (Print Screen, Gnome Screenshot, etc.)

### If something doesn't work
1. **Read the error in console**
2. **Check container logs:** `docker logs <NAME>`
3. **Verify the command:** make sure it's copied correctly
4. **Clean and redo:** `docker rm <NAME> && docker run ...`
5. **Check reference:** [DOCKER_COMMANDS_REFERENCE.md](DOCKER_COMMANDS_REFERENCE.md)

---

## 🔍 How to use the files in this repository

### File: [TASKS_GUIDE_EN.md](TASKS_GUIDE_EN.md)
**English reference** with all commands - use as reference

### Files: [Part_A/README_EN.md](Part_A/README_EN.md) and [Part_B/README_EN.md](Part_B/README_EN.md)
**Detailed instructions** with required screenshots for each task

### File: [DOCKER_COMMANDS_REFERENCE.md](DOCKER_COMMANDS_REFERENCE.md)
**Docker command reference** - look here if you forgot the syntax

### This file (INSTRUCTIONS_EN.md)
**Instructions and action plan** - start here!

---

## ✨ Ready to work!

You're all set! Go to [Part_A/README_EN.md](Part_A/README_EN.md) and follow the instructions there.

**Good luck with the assignment! 🎯**
