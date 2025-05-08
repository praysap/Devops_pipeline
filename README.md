# 🚀 DevOps CI/CD Pipeline

This project demonstrates a simple **CI/CD pipeline** that automatically pulls and deploys changes from a GitHub repository using **Python**, **Shell scripting**, and **cron jobs**, with `nginx` serving a static `index.html` page.

---

## 📁 Project Structure

```
CI-CD_Pipeline_Tool/
│-- python&shellScripting/
│   ├── check_commits.py     # Script to check for new commits
│   ├── deploy.sh            # Deployment script
│-- .gitignore               # Git ignore file
│-- index.html               # Sample index page
│-- README.md                # Project documentation
```
---

## ✨ Features

- 🔁 **Automated Commit Checking** via `check_commits.py`
- 🚚 **Auto Deployment** using `deploy.sh`
- ⏱️ **Cron Job Integration** for periodic execution
- 🌐 **Nginx Setup** to serve static content
- 🔐 **Token-Based GitHub Authentication**
- 📄 **Execution Logging** for audit and debugging

---

## 🧰 System Requirements

Ensure the following are installed on your Ubuntu/Linux system:

```bash
sudo apt update
sudo apt install -y nginx git python3 pipx
pipx ensurepath
```
---

## Project Setup

1. Set up your Github Token with GitHub.
2. Clone the repository:
   ```bash
   cd /var/www/html/
   git clone <your_repo_url>
   cd CI-CD_Pipeline_Tool
   ```
3. Create a `log` directory:
   ```bash
   mkdir log && chmod 755 log
   ```

4. Copy the provided scripts:
   - `check_commits.py`
   - `deploy.sh`  
   (Refer to `deploy_sample/`)

5. Make both scripts executable:
   ```bash
   chmod 755 check_commits.py deploy.sh
   ```
---

## GitHub Token Setup

### On Ubuntu:
1. Install `python3-dotenv`:
   ```bash
   sudo apt install -y python3-dotenv
   ```
2. Create a `.env` file and add your GitHub token:
   ```python
   GITHUB_TOKEN = "your_github_token"
   ```
3. Ensure `.env` is listed in `.gitignore`.

### On Windows:
1. Install dotenv:
   ```bash
   pip install python-dotenv
   ```
2. Create a `.env` file and add your GitHub token:
   ```python
   GITHUB_TOKEN = "your_github_token"
   ```
3. Ensure `.env` is listed in `.gitignore`.
---

## Nginx Setup

1. Update Nginx configuration:

```bash
sudo nano /etc/nginx/sites-available/default
```

2. Set the root to:

```nginx
root var/www/html/Devops_pipeline/;
```


## Cron Job Setup (Every 5 Minutes)

1. Edit crontab:

```bash
crontab -e
```


2. Add the following line (adjust paths as needed):

```cron
*/5 * * * * /usr/bin/python3 /var/www/html/check_commits.py >> /var/www/html/log/check_commits.log 2>&1
```

4. Validate Cron:

```bash
crontab -l
systemctl status cron
```
---

## Askpass Script (Optional for Sudo Automation)

1. Create an askpass script for secure sudo:

```bash
nano ~/askpass.sh
```

2. Add the following:

```bash
#!/bin/bash
echo "your_sudo_password"
```

3. Make it executable:

```bash
chmod +x ~/askpass.sh
```
---

## Validation Snapshots
1. Project Repo directories and files:<br>
<img width="499" alt="image" src="https://github.com/user-attachments/assets/0bd0fd5d-d139-4fa3-9081-39aff0f2f366" /><br>

2. Github token setup in .env file:<br>
<img width="611" alt="image" src="https://github.com/user-attachments/assets/4649dfbf-faef-4c39-9ade-da32af9acea6" /><br>

3. Nginx setup:<br>
<img width="806" alt="image" src="https://github.com/user-attachments/assets/80215aa9-319f-44eb-9fd8-700f496b3a04" /><br>

4. Crontab setup:<br>
<img width="851" alt="image" src="https://github.com/user-attachments/assets/b7392a59-fb64-4fdc-92c0-03cd1509b5d3" /><br>

5. Log directory files:<br>
<img width="562" alt="image" src="https://github.com/user-attachments/assets/6cfa5eb1-de86-443f-9855-8867a7976215" /><br>

6. Latest Commit details storing in a file (latest_commit.txt):<br>
<img width="629" alt="image" src="https://github.com/user-attachments/assets/62b3080c-4b35-4627-ab08-e6fd0775cf13" /><br>

7. Deployment logs storing in a file (deploy.log):<br>
<img width="521" alt="image" src="https://github.com/user-attachments/assets/9693ef72-9d92-47f0-8691-e7f7f4b52fba" /><br>

8. Checking commits to do the latest deployment on the server (checking_commits.log):<br>
<img width="682" alt="image" src="https://github.com/user-attachments/assets/085e0134-67ec-4c55-8c41-49d2a9d398c6" /><br>
![image](https://github.com/user-attachments/assets/c65388cb-a74d-4026-bb16-5f2bd78e42c7)<br>
---

## 📄 License

