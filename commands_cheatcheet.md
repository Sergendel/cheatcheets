# 📌 Cheat Sheet: Git and Docker Commands

## 🚀 Git Commands

| ``                                  |                                               | ``                                                                                  | 
| Command                             | Description                                   | Example                                                                             |
|--------------------------------     |-----------------------------------------------|-------------------------------------------------------------------------------------|
| `git init`                          | Initialize new Git repository                 | `git init`                                                                          |
| `git add <file>`                    | Stage changes for commit                      | `git add file.txt`   or add all by git add .                                        |
| `git commit -m "msg"`               | Commit changes with message                   | `git commit -m "Add initial commands cheatsheet"`                                   | 
| `git remote add origin <link>`      | Links local repo to remote repo URL           | `git remote add origin https://github.com/Sergendel/cheatcheets.git`                |
| `git remote -v`                     | Shows  all remote repos connected             | `git remote -v`  -v for verboes - (names+url)                                       |
| `git branch -a`                     | List all branches                             | `git branch -a`                                                                     |
| `git branch -M main`                | Rename (forced) of the current branch         | `git branch -M main` rename master to main                                          |
| `git status`                        | Check repository status                       | `git status`                                                                        | 
| `git push -u origin main`           | -u sets local branch to follow remote branch. |  Now Git remembers the relationship                                                 |
| `git push`                          | Sends local commits to the remote repo        | `git push`                                                                          |
| `git mv oldname.md newname.md`      | Renames the file locally                      |                                                                                     |
| `git clone <repo>`                  | Clone a repository                            | `git clone https://github.com/user/repo.git`                                        |      
| `git pull`                          | Pull changes from remote                      | `git pull origin main`                                                              |
| `git branch <name>`                 | Create a new branch                           | `git branch feature1`                                                               |
| `git checkout <branch>`             | Switch to branch                              | `git checkout feature1`                                                             |
| `git merge <branch>`                | Merge a branch into current                   | `git merge feature1`                                                                |
| `git rm <file>`                     | remove file from Git                          | ``                                                                                  | 
                    
                    
## Python installation                  
| ``                                  |                                               | ``                                                                                  | 
| Command                             | Description                                   | Example                                                                             |
|--------------------------------     |-----------------------------------------------|-------------------------------------------------------------------------------------|
| `python --version`                  | Verify python version                /c/Users/serge/AppData/Local/Programs/Python/Python37/python.exe --version                     | 
| `pip --version`                     |                                               | ``                                                                                  | 
               
               
               
               
## Python env                 
| ``                                  |                                               | ``                                                                                  | 
| Command                             | Description                                   | Example                                                                             |
|--------------------------------     |-----------------------------------------------|-------------------------------------------------------------------------------------|
| `python -m venv <env_name>`         | Create new Python env                         | `python -m venv rl_lunar_lander_expected_sarsa_env`                                 |
| `<Python link> -m venv <env_name>`  | Use specific python version for env creation  |/c/Users/your-username/AppData/Local/Programs/Python/Python37/python.exe -m venv env |
| `source env/Skripts/activate`       | Activate env  (in GitBash)                    | `source rl_env/Scripts/activate`                                                    |
| `pip install -r requirements.txt`   | Install All Required Packages                 | ``                                                                                  |


## conda
| ``                                  |                                               | ``                                                                                  | 
| Command                             | Description                                   | Example                                                                             |
|--------------------------------     |-----------------------------------------------|-------------------------------------------------------------------------------------|
| `conda --version`                   |                                               | ``                                                                                  |
| `conda create -n env python=3.7.6`  | Creates env with specific Python version      |  Don’t need the Python version pre-installed  on the system                         |
| `conda activate env`                | Activate  environment                         | `$conda activate lunar_lander_expected_sarsa_env`                                   |
| `conda list`                        | Confirm Installed Packages                    | ``                                                                                  |
| `conda install gmpy2 -c conda-forge`| Install package from the conda-forge channel  | ``                                                                                  |
| `conda install --file requirements.txt -c conda-forge`                              | Install all packages from your requirements.txt via Conda                           | 
| `pip install -r requirements.txt`   | Install any packages Conda skipped            | ``                                                                                  |
|` pip list`                          |                                               | ``                                                                                  | 
| `conda env export > environment.yml`| Export your Conda environment:                | `RUN conda env create -f environment.yml`  usage in docker file                     | 
| `conda deactivate`                  |                                               | ``                                                                                  | 
| `conda remove --name myenv --all`   |                                               | ``                                                                                  | 
| `conda info --envs`                 |   Verify Conda Environment Path               | ``                                                                                  | 



## 🐳 Docker Commands

### **Container Management**
1. simple build with no volumes, image runs as it is 
docker build . -t lunar:v1              build image 
docker images                           verify image
docker run -it lunar:v1 


| Command                                       | Description                                 | Example                                  |
|-----------------------------------------------|---------------------------------------------|------------------------------------------|
| `docker build -t <name> .`                    | Build Docker image with name                | `docker build -t myapp:v1 .`             |
| `docker run <image>`                          | Run container from image                    | `docker run ubuntu`                      |
| `docker ps`                                   | List running containers                     | `docker ps`                              |
| `docker ps -a`                                | List all containers                         | `docker ps -a`                           |
| `docker stop <container_id>`                  | Stop container                              | `docker stop abc123`                     |
| `docker rm <container_id>`                    | Remove container                            | `docker rm abc123`                       |
| `docker rmi <image>`                          | Remove image                                | `docker rmi myapp:v1`                    |
| `docker system df`                            | Overview  of Docker's disk usage            |                                          |
| `docker system prune -a --volumes`            | reclaim disk space explicitly safely        | delete unused images, cont-s, netw-s, ...|

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


# 🎧 FitBeat: LLM-Powered Music Recommendation Agent

**Author:** Sergey Gendel

---

## 🚀 Project Overview

**FitBeat** is an LLM-powered Music Recommendation Agent transforming emotional or situational descriptions (e.g., "music for intense gym training" or "playlist for a child's birthday party") into personalized playlists.

## 🛠️ Technology Stack

FitBeat leverages a modern, powerful tech stack, explicitly designed to demonstrate cutting-edge ML, LLM, and MLOps capabilities:

* **Languages & Libraries:** Python, FastAPI, PyTorch, Transformers, Sentence-Transformers, OpenAI API, Genius API
* **Machine Learning Techniques:** Retrieval-Augmented Generation (RAG), Embedding-based Semantic Ranking
* **Cloud Infrastructure:** AWS Lambda, AWS API Gateway, AWS S3, AWS Secrets Manager, AWS CloudWatch
* **Deployment Tools:** AWS Serverless Application Model (SAM), Docker, GitHub Actions (CI/CD)
* **Testing & Quality:** Pytest, Flake8, Black, Isort

---

## 📌 How It Works (Quick Overview)

### 1. Initial Filtering (Numeric Analysis)

* Converts prompts into numeric audio features (tempo, energy, etc.).
* Filters from a large Kaggle [Spotify Tracks Dataset](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset).

### 2. Hybrid Semantic Ranking (Embeddings & RAG)

* Retrieves track lyrics and descriptions from [Genius](https://genius.com/).
* Ranks tracks by semantic similarity using embeddings and RAG-based refinement.

### 3. Final Recommendation & Output

* Provides structured recommendation table (Artist, Track Name, YouTube link).
* Optionally downloads and converts tracks to MP3 if configured (`FRONTEND_MODE=False`).

---

## 🚀 Agent's Internal Workflow

FitBeat operates via a structured LLM-driven pipeline:

### 1. Memory Initialization (Optional)

### 2. Action Plan Creation

### 3. Action Plan Structuring (JSON)

### 4. Execute Actions (via dedicated agent tools)

---

## ⚙️ Agent Tools

* Numeric Filtering
* Hybrid Semantic Ranking (Embeddings & RAG)
* Recommendation Table Creation
* Track Retrieval & Conversion (optional)
* Playlist Summarization

---

## 🧠 Agent Memory (Persistent Context Management)

FitBeat maintains context across interactions, summarizing prompts and storing summaries (`conversation_memory.json`).

---

## 🧪 Testing and CI/CD

* **Unit & E2E Testing**: Using Pytest and GitHub Actions
* **Code Quality**: Flake8, Black, Isort

---

## 📦 Deployment and Usage (Single-Lambda AWS Deployment)

### ✅ Deployment Overview

FitBeat is deployed explicitly using AWS SAM, packaged as a Docker container hosted on AWS Lambda, accessible via AWS API Gateway.

**Live API endpoints:**

* **Status Check (`GET`):**

  ```
  https://cnrf43xfm8.execute-api.us-east-1.amazonaws.com/Prod/status
  ```
* **Music Recommendation (`POST`):**

  ```
  https://cnrf43xfm8.execute-api.us-east-1.amazonaws.com/Prod/recommend
  ```

### ✅ Testing the Deployed API

**Using Curl:**

Status endpoint:

```bash
curl https://cnrf43xfm8.execute-api.us-east-1.amazonaws.com/Prod/status
```

Recommend endpoint:

```bash
curl -X POST https://cnrf43xfm8.execute-api.us-east-1.amazonaws.com/Prod/recommend \
     -H "Content-Type: application/json" \
     -d '{"description": "upbeat music for intense gym training", "clear_memory": true}'
```

**Using Postman:**

1. Open Postman and create a new HTTP Request.
2. Set method to `POST` and URL to:

   ```
   https://cnrf43xfm8.execute-api.us-east-1.amazonaws.com/Prod/recommend
   ```
3. In "Headers", add:

   ```
   Key: Content-Type
   Value: application/json
   ```
4. Under "Body", select "raw" and "JSON", and paste:

   ```json
   {
     "description": "upbeat music for intense gym training",
     "clear_memory": true
   }
   ```
5. Click "Send" and view your recommended playlist response.

*(Consider adding Postman request/response screenshots for clarity.)*

---

## 🚀 How to Run (Local Development)

### ✅ Clone the Repository

```bash
git clone https://github.com/your-repo/FitBeat.git
cd FitBeat
```

### ✅ Install Requirements

```bash
pip install -r requirements.txt
```

### ✅ API Keys Configuration

Copy `.env.example` to `.env` and insert your keys:

```ini
OPENAI_API_KEY="your-openai-api-key"
GENIUS_API_KEY="your-genius-api-key"
```

### ✅ Run Application Locally

```bash
python -m core.orchestrator
```

---
