# DevOps_Tasks
# 📦 Task #1

## 📄 What the Script Does

This Python script automates the following tasks:

### ✅ Step 1: Download ZIPs of All Branches
- For every repository under a given GitHub user/org, the script downloads ZIP files for **all branches**.

### ✅ Step 2: Upload ZIPs to Google Drive
- All ZIPs are uploaded to a **Google Drive folder** using `pydrive`.

### ✅ Step 3: Intelligent Re-Download with Checksum Detection
- Before downloading, it checks if a ZIP file for a `repository-branch` combo has **changed** (based on SHA256 checksum).
- Downloads and uploads only if there is a change.

### ✅ Step 4: Google Drive Upload (Final)
- Only the ZIPs with **changed content** are uploaded to your specified Google Drive folder.

> ℹ️ This script is intended to run **daily via cron or automation** for optimal performance.

---
## 🔐 Google Drive Setup (PyDrive Auth)
* Go to Google Cloud Console.
* Create a project > Enable Google Drive API.
* Create OAuth 2.0 credentials.
* Download client_secrets.json and place it in the project directory.
* Add test users in OAuth consent screen and add your mail account otherwise it will give error.
* The first time you run the script, a browser will open to authenticate and save credentials.json.
---
## 📂 What the Scripts Do
### ✅ task1.py
* Fetches all repositories and their branches for a given GitHub username.
* Downloads each repository branch as a ZIP file into the downloaded_zips/ folder.
* Can be scheduled to run daily to keep local copies updated.
* Uses GitHub Personal Access Token (PAT) to authenticate API requests and bypass rate limiting.

### ✅ task1.1.py
* Calculates SHA256 checksums of downloaded zip files.
* Only uploads files to Google Drive if they have changed since the last run.
* Saves current checksums in checksums.json.
* Connects to Google Drive using OAuth 2.0 with PyDrive:
    - Uses client_secrets.json to initiate the authentication.
    - On first run, prompts for Google login in a browser window.
    - After successful login, creates a persistent credentials.json file for future use.
---
## 📦 Output
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/c695d4c5-4227-416e-b63d-ad297254e2b1" />
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/41ba2281-8c9f-4c4b-8e7f-30bf8d4402e1" />

---
# 📊 Task #2

## 📄 What the Script Does

This Python script analyzes **code contribution data (lines of code added, removed, or updated)** for a public GitHub repository.

### ✅ Features:
- Fetches contributor activity using the GitHub API.
- Aggregates **weekly line changes** (added, deleted, total) for each contributor.
- Filters data from **01-Jan-2023** to the **current date**.
- Displays contributions **per week per contributor**.

> ⚠️ **Note:** GitHub's API may take **a few minutes** to generate and return statistics for large or inactive repositories. Please be patient after execution.

---
## 📦 Output
Here's output of one of my repository
<img width="757" height="321" alt="image" src="https://github.com/user-attachments/assets/e77a138a-9801-42df-9af9-06e3a4e14eec" />

---
# 🚀 Task #3

## 📄 What the Script Does

This Python script analyzes a Linux system's SSH log file (typically `/var/log/auth.log`) and performs the following:

1. ✅ **Extracts successful SSH login attempts** using public key authentication.
   - Captures: **Username**, **IP Address**, **Port**, and **Timestamp**.
2. ✅ **Identifies failed login attempts** due to **key mismatch** (invalid or unaccepted public keys).
3. ✅ Outputs all collected entries into a CSV file named `ssh_logins.csv`.

> ℹ️ **Note:** In the provided `auth.log`, there were no actual "key mismatch" logs. Therefore, for demonstration and testing purposes, i insert one **rejected key entry** to verify the script works as expected.

---
