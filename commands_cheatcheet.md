# 📌 Cheat Sheet: Git and Docker Commands

## 🚀 Git Commands
| ``                             |                                               | ``                                                                   | 
| Command                        | Description                                   | Example                                                              |
|--------------------------------|-----------------------------------------      |--------------------------------------------------------------------  |
| `git init`                     | Initialize new Git repository                 | `git init`                                                           |
| `git add <file>`               | Stage changes for commit                      | `git add file.txt`   or add all by git add .                         |
| `git commit -m "msg"`          | Commit changes with message                   | `git commit -m "Add initial commands cheatsheet"`                    | 
| `git remote add origin <link>` | Links local repo to remote repo URL           | `git remote add origin https://github.com/Sergendel/cheatcheets.git` |
| `git remote -v`                | Shows  all remote repos connected             | `git remote -v`  -v for verboes - (names+url)                        |
| `git branch -a`                | List all branches                             | `git branch -a`                                                      |
| `git branch -M main`           | Rename (forced) of the current branch         | `git branch -M main` rename master to main                           |
| `git status`                   | Check repository status                       | `git status`                                                         | 
| `git push -u origin main`      | -u sets local branch to follow remote branch. |  Now Git remembers the relationship                                  |
| `git push`                     | Sends local commits to the remote repo        | `git push`                                                           |
| `git clone <repo>`             | Clone a repository                            | `git clone https://github.com/user/repo.git`                         |      
| `git pull`                     | Pull changes from remote                      | `git pull origin main`                                               |
| `git branch <name>`            | Create a new branch                           | `git branch feature1`                                                |
| `git checkout <branch>`        | Switch to branch                              | `git checkout feature1`                                              |
| `git merge <branch>`           | Merge a branch into current                   | `git merge feature1`                                                 |




## 🐳 Docker Commands

### **Container Management**

| Command                                       | Description                                 | Example                                  |
|-----------------------------------------------|---------------------------------------------|------------------------------------------|
| `docker build -t <name> .`                    | Build Docker image with name                | `docker build -t myapp:v1 .`             |
| `docker run <image>`                          | Run container from image                    | `docker run ubuntu`                      |
| `docker ps`                                   | List running containers                     | `docker ps`                              |
| `docker ps -a`                                | List all containers                         | `docker ps -a`                           |
| `docker stop <container_id>`                  | Stop container                              | `docker stop abc123`                     |
| `docker rm <container_id>`                    | Remove container                            | `docker rm abc123`                       |
| `docker rmi <image>`                          | Remove image                                | `docker rmi myapp:v1`                    |

### **Volume Mounting**

| Command                                                               | Description                                          | Example                                                   |
|-----------------------------------------------------------------------|------------------------------------------------------|-----------------------------------------------------------|
| `docker run -v host_path:container_path <image>`                      | Mount volume (simple)                                | `docker run -v /local/data:/data ubuntu`                  |
| `docker run --mount type=bind,source=host_path,target=container_path <image>` | Mount volume (explicit syntax)                       | `docker run --mount type=bind,source=/local/data,target=/data ubuntu` |
| `docker run --mount type=volume,source=vol_name,target=container_path <image>` | Mount named Docker volume                            | `docker run --mount type=volume,source=myvol,target=/data ubuntu` |

---

### **Docker Flags (Common)**

| Flag | Meaning                              | Example                                   |
|------|--------------------------------------|-------------------------------------------|
| `-i` | Interactive mode (keeps STDIN open)  | `docker run -i ubuntu`                    |
| `-t` | Allocates pseudo-TTY (interactive)   | `docker run -it ubuntu`                   |
| `-d` | Detached mode (run in background)    | `docker run -d ubuntu`                    |
| `-p` | Publish container port to host       | `docker run -p 8080:80 nginx`             |

---
