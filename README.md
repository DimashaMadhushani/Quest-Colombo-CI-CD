# 🚀 Quest Colombo CI/CD Pipeline

This repository contains the Jenkins CI/CD pipeline configuration for the Quest Colombo full-stack web application. The application includes a React.js frontend, Node.js backend, and MySQL database.


##  Tech Stack

- **Frontend**: React.js + Vite
- **Backend**: Node.js + Express
- **Database**: MySQL (managed via Laravel migrations)
- **CI/CD**: Jenkins


##  How to Set Up the Jenkins Environment

1. **Install Prerequisites**:
   - Java JDK 17
   - Git
   - Node.js + npm
   - MySQL Server
   - Jenkins (Windows/WSL)

2. **Configure Jenkins**:
   - Install plugins: Git, NodeJS, Pipeline
   - Set up NodeJS under "Global Tool Configuration"
   - Create a pipeline job using this repo

3. **Database Setup**:
   - MySQL schema is managed via **Laravel migration files**
   - Run: `php artisan migrate` to auto-create all necessary tables


##  Pipeline Stages

1. ✅ Clone Frontend & Backend
2. ✅ Install npm dependencies
3. ✅ Run Tests (skipped if no test scripts)
4. ✅ Build Frontend
5. ✅ Start Backend
6. ✅ Create Pipeline in Jenkins
7. ✅ Run Jenkins Pipeline


##  Project Repos

- 🔗 [Frontend](https://github.com/DimashaMadhushani/Quest-Colombo-Frontend)
- 🔗 [Backend](https://github.com/DimashaMadhushani/Quest-Colombo-API)
- 🔗 [CI/CD Jenkinsfile](https://github.com/DimashaMadhushani/Quest-Colombo-CI-CD)
  

##  Challenges & Fixes

⚙️ NodeJS auto-install failed in Jenkins → Installed manually & set path
⚙️ Missing SVG during frontend build → Removed broken image import
⚙️ start command failed on Linux → Replaced with nohup node index.js &
⚙️ Git push conflicts → Resolved with --allow-unrelated-histories
⚙️ Duplicate stages {} block → Merged all stages under one block


##  How to Replicate

```bash
git clone https://github.com/DimashaMadhushani/Quest-Colombo-CI-CD.git
cd Quest-Colombo-CI-CD
# Jenkins will read the Jenkinsfile from here
