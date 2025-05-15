# Day-15

# Ansible:

# 1. Installed Ansible:

- click  [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-ubuntu-20-04)


# 2. Setup Password-less Authentication in Ansible using SSH Keys:

### prerequisite:

- create two EC2 instances Contorl Node & Managed Node.

### 🖥️ Scenario:

* You're on **Control Node** (e.g., your laptop).
* You can open another terminal and log into the **Managed Node**.
* You want to manually **copy the Control Node’s public key** into the Managed Node’s `authorized_keys` file.

> The **Control Node's public key** is copied to the **Managed Node’s `authorized_keys`** file. This allows the Control Node to log in **without a password**.


### 🖥️ What is Control Node and Managed Node?

| Term             | Meaning                                                                          |
| ---------------- | -------------------------------------------------------------------------------- |
| **Control Node** | Your system where **Ansible is installed**. It sends commands.                   |
| **Managed Node** | Remote server (like EC2, Ubuntu server, etc.) you want to control using Ansible. |

---

## 🔄 Step-by-Step Flow:

### ✅ Step 1: Generate SSH Key on Control Node (if not already done)

On the **Control Node**:

```bash
ssh-keygen
```

* Press Enter for default location: `~/.ssh/id_rsa`
* Do **not** enter any passphrase (just hit Enter)

This creates:

* `~/.ssh/id_rsa` → private key
* `~/.ssh/id_rsa.pub` → public key

---

### ✅ Step 2: View the Public Key on Control Node

```bash
cat ~/.ssh/id_rsa.pub
```

Example output:

```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC... your_key_here ... user@hostname
```

---

### ✅ Step 3: Open a Second Terminal → Log into the Managed Node

```bash
ssh user@managed-node-ip
```

Example:

```bash
ssh ubuntu@192.168.1.10
```

Now you're inside the Managed Node terminal.

---

### ✅ Step 4: Create the `.ssh` directory (if not exists)

On the **Managed Node**:

```bash
mkdir -p ~/.ssh
chmod 700 ~/.ssh
```


### ✅ Step 5: Open `authorized_keys` file in a text editor

use `vim` :

```bash
vi ~/.ssh/authorized_keys
```


### ✅ Step 6: Paste the Public Key

* From the Control Node’s terminal, **copy** the full output of:

```bash
cat ~/.ssh/id_rsa.pub
```

* Then **paste** it into the `authorized_keys` file in the Managed Node’s terminal.


### ✅ Step 7: Save and Set Permissions

After saving the file:

```bash
chmod 600 ~/.ssh/authorized_keys
```

✅ Done! Now exit the Managed Node:

```bash
exit
```

### ✅ Step 8: Test the SSH Login (Password-less)

Back on the Control Node:

```bash
ssh user@managed-node-ip
```

It should **log in without asking for a password**.


### Summary

| Action                           | Performed On                |
| -------------------------------- | --------------------------- |
| Generate SSH Key                 | Control Node                |
| Copy public key (manually)       | Control Node → Managed Node |
| Paste key into `authorized_keys` | Managed Node                |
| Test SSH                         | Control Node                |




