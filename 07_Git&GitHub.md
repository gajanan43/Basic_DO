# Day-09

## What is a Version Control System (VCS)?

A Version Control System (VCS) is a tool that helps manage changes to files, especially code, over time. 
It keeps track of every modification made to the codebase, so you can:

- ```View the history``` of changes
- ```Revert``` to previous versions if needed
- ```Collaborate``` with others without overwriting each other’s work


### Types of Version Control Systems:

1. **Local VCS**: Stores versions on a local system (e.g., RCS).
2. **Centralized VCS**: Uses a central server (e.g., SVN, CVS).
3. **Distributed VCS**: Every user has a full copy of the repository (e.g., **Git**).


## Key Features of a VCS:

* **Tracking changes** in files (who changed what and when)
* **Branching and merging** to allow simultaneous work on different features
* **Backup and recovery** by storing historical versions
* **Collaboration** among multiple developers


### Popular VCS Tools:

* **Git** (most popular, distributed)
* **Subversion (SVN)** (centralized)
* **Mercurial**
* **Perforce**


## Centralized Version Control System (CVCS)

* There is **one central server** where all the code and history are stored.
* Developers **connect to this server** to get the latest code or share their changes.
* If the **server goes down**, no one can collaborate or access the code.

**Example:** SVN (Subversion), CVS

#### Think of it like:

A classroom with **one whiteboard** (the server). Everyone must go to that whiteboard to see or update information. If the whiteboard is gone, no one can work.


## 🔹 Distributed Version Control System (DVCS)

* Every developer has a **full copy of the entire project**, including the history.
* You can **work offline** — commit changes, switch branches, and view history.
* When ready, you can **sync with others** using a remote server (like GitHub).

**Example:** Git, Mercurial

####  Think of it like:

Every student in the classroom has their **own notebook** with a full copy of the whiteboard. They can work on their own and later share updates with each other.


![ChatGPT Image May 12, 2025, 08_01_40 PM](https://github.com/user-attachments/assets/fdef92cf-4efd-4e15-9d6f-9f35bae105ce)

