# Day-11

## 1.How to Create or Initialize a Git Repository?
   
   git init    → Initializes a new Git repository in the current folder.

- ```ls -a``` → Lists all files, including hidden ones (you will see .git folder).

- ```ls -ltra``` → Lists all files with detailed information.

- ```git status``` → Shows the current status of the repository (modified, staged, etc.).
- ```git diff``` → Shows the differences between the working directory and the last commit.

- ```git add <file>``` → Adds a file to the staging area.
- ```git checkout <branch>``` → Switches to another branch.
- ```git checkout -b new_branch_name```  → To Create and Switch to a New Branch
- ```git switch -c new_branch_name```

- ```git commit -m "message"``` → Saves the changes to the repository with a message.

- ```git log``` → Shows the history of commits.
- ```git push``` → Uploads local commits to a remote repository.
- ```git clone <repo-url>``` → Downloads (copies) a remote repository to the local system.
- ```git remote -v``` → Displays the remote repositories linked to your local repo.
- ```ssh-keygen -t rsa``` → Generates an SSH key for secure Git authentication.
- ```git rm file_name```  →to remove form directory

## How to push file on github?

 1) create folder    →  Create a new folder
 2) create file      →  Create or add your file
 3) git init         →  Initialize Git repo
 4) git add.         →  Add files to Git
 5) git commit -m "message"  →  Commit your changes
 6) git remote add origin https://github.com/yourusername/test-project.git  →  Connect to GitHub repository
 7) git branch -M main       →  
 8) git push -u origin main  →  Push to GitHub

## 2. Difference Between Clone and Fork
- Fork → Creates a separate copy of a repository in your GitHub/GitLab account (used for contributing to open-source projects).
- Clone → Downloads an existing repository from GitHub to your local machine for development.
 
## 3. Explain Git Lifecycle
Git follows these four main stages:

- Untracked → Files are created but not yet tracked by Git.
- Modified → Files are tracked but have unsaved changes.
- Staged → Files are added to the staging area using git add.
- Committed → Changes are saved in the repository using git commit.
  
## 4. Why Do We Create a New Branch?
- To work on a new feature or fix a bug without affecting the main branch.
- To allow multiple developers to work on different features independently.
  
## 5. Merge, Rebase, and Cherry-Pick
- Merge (git merge) → Combines changes from one branch into another.
- Rebase (git rebase) → Moves a branch to start from a new base, making the commit history cleaner.
- Cherry-Pick (```git cherry-pick <commit-hash>```) → Selectively applies specific commits from one branch to another.
  
## 6. Difference Between Merge and Rebase
- Merge → Creates a new commit that combines both branch histories.
- Rebase → Reapplies commits on top of another branch, making history linear (no extra merge commits).
