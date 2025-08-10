# **DevOps Project: Git Workflow Demo**

This repository is a practical demonstration of a standard Git workflow. The goal was to manage a simple web project using best practices like feature branching, pull requests, and version tagging to ensure a clean and stable codebase.

***

## **Workflow and Steps Executed**

We followed a structured branching model to manage changes from development to production.

1.  **Repository Initialization**: A local Git repository was created using `git init` and connected to this remote GitHub repository.
2.  **Branching Strategy**: A standard branching model (`main`, `dev`, `feature/*`) was established to isolate work and maintain a stable production branch.
3.  **Development and Commits**: Initial project files (`index.html`, `.gitignore`) were created and modified on a dedicated `feature` branch.
4.  **Pull Requests (PRs)**: Pull requests were used to manage code review and merge changes first from `feature` to `dev`, and then from `dev` to `main`.
5.  **Tagging**: Once the final changes were merged into `main`, a tag `v1.0` was created to mark this specific release version.

***

## **Terminal Command Log**

This is the complete log of terminal commands used to execute the workflow.

```bash
# Navigate into the project folder
cd my-devops-project

# Initialize a new local Git repository
git init

# Connect the local repository to the remote one on GitHub
git remote add origin [https://github.com/ash13579/my-devops-project.git](https://github.com/YOUR_USERNAME/my-devops-project.git)

# Set the default branch name to 'main'
git branch -M main

# --- First Commit ---
# (After creating index.html, README.md, .gitignore)
# Stage all new files for the first commit
git add .
# Create the first commit, which officially creates the 'main' branch
git commit -m "Initial commit: Add project structure"

# --- Branching ---
# Create the development branch from main
git branch dev
# Create and switch to a new feature branch from dev
git checkout -b feature/add-header

# --- Making Changes on the Feature Branch ---
# (After modifying index.html)
# Stage the changes
git add index.html
# Commit the feature changes
git commit -m "feat: Add introductory paragraph to homepage"

# --- Pushing Branches to GitHub ---
# Push the new feature branch and set its upstream tracking branch
git push -u origin feature/add-header
# Switch to the dev branch and push it
git checkout dev
git push -u origin dev
# Switch to the main branch and push it
git checkout main
git push -u origin main

# --- Tagging a Release ---
# (After merging PRs on GitHub)
# Switch back to the main branch locally
git checkout main
# Pull the latest changes from GitHub (which includes the merged PRs)
git pull origin main
# Create a new annotated tag for version 1.0
git tag -a v1.0 -m "Version 1.0 release"
# Push the new tag to GitHub
git push origin v1.0
