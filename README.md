# ECE260B Project

## **Branching Strategy**
We are using the following branches:
- **`main`** - The production-ready branch (Only merged after review).
- **`scratch`** - The working branch where all collaborators push their changes before review.

All work must go into the `scratch` branch first. The `main` branch should only be updated via reviewed merges from `scratch`.

---

## **Initial Setup (One-Time Only)**
Each collaborator should perform this setup once:
```sh
# Clone the repository
git clone <repo-url>
cd <repo-folder>

# Switch to the scratch branch
git checkout -b scratch origin/scratch
```

## **Personal Access Token:**
Each collaborator needs to generate a personal access token and need to use this as the password every time they push code along with their username. This is only shown once so generate it and save it somewhere so that you can reuse it.

### Steps to Generate a PAT:

1.  Log in to GitHub and go to Settings.

2.  Navigate to Developer settings > Personal access tokens.

3.  Click "Generate new token" and provide a descriptive name.

4.  Select an expiration date (recommended: 30 or 90 days).

5.  Choose necessary permissions (e.g., repo for repository access).

6.  Click "Generate token" and copy it immediately.
---

## **Daily Workflow**

### **1. Ensure Your Local Repo is Up-to-Date**
Before making changes, update your local `scratch` branch:
```sh
git checkout scratch  # Switch to scratch branch
git pull origin scratch  # Get the latest updates
```

### **2. Make Changes and Commit**
After modifying files:
```sh
git add .  # Stage all changed files
git commit -m "Descriptive commit message"  # Commit your changes
```

### **3. Sync With the Latest `scratch` (To Avoid Conflicts)**
Before pushing, ensure your branch is up to date:
```sh
git pull origin scratch  # Get the latest changes
```
If conflicts occur, resolve them manually, then:
```sh
git add .  # Stage resolved files
git commit -m "Resolved merge conflicts"
```

### **4. Double Check Which Branch You Are Pushing Into**
```sh
git status  # Shows all the differences between your branch and the latset one
```

### **5. Push Your Changes to `scratch`**
Once your changes are committed:
```sh
git push origin scratch  # Push the updated scratch branch
```

---

## **Handling Push Conflicts (If Someone Else Pushed First)**
If you try to push and get a rejection error (`rejected` message), do the following:
```sh
git pull origin scratch --rebase  # Pull latest changes and reapply your commits
```
If conflicts occur, resolve them manually, then:
```sh
git add .  # Stage resolved conflicts
git rebase --continue  # Continue after resolving conflicts
git push origin scratch  # Push your changes
```

---

## **Final Merge to Main (By Maintainer)**
Once all changes are reviewed and approved, the maintainer will merge `scratch` into `main`:
```sh
git checkout main  # Switch to main

git pull origin main  # Ensure the latest version

git merge scratch  # Merge scratch into main

git push origin main  # Push the updated main branch
```



