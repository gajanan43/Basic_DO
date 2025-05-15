# Day-15

## 1. Installed Ansible:

- click  [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-ubuntu-20-04)


## 🔐 Password-less Authentication in Ansible using SSH Keys

### 🧠 Idea:

> The **Control Node's public key** is copied to the **Managed Node’s `authorized_keys`** file. This allows the Control Node to log in **without a password**.

---

## 🖥️ What is Control Node and Managed Node?

| Term             | Meaning                                                                          |
| ---------------- | -------------------------------------------------------------------------------- |
| **Control Node** | Your system where **Ansible is installed**. It sends commands.                   |
| **Managed Node** | Remote server (like EC2, Ubuntu server, etc.) you want to control using Ansible. |

---

## 🔄 Step-by-Step Flow:

### ✅ Step 1: Generate SSH Key on the **Control Node**

```bash
ssh-keygen
```

* This creates a **public key** and a **private key**:

  * Public Key: `~/.ssh/id_rsa.pub`
  * Private Key: `~/.ssh/id_rsa`

👉 **The public key will be shared**, the private key is kept secret.

---

### ✅ Step 2: Copy the **Control Node's public key** to the **Managed Node**

Run this command on the Control Node:

```bash
ssh-copy-id user@managed-node-ip
```

Example:

```bash
ssh-copy-id ubuntu@192.168.1.10
```

👉 This will copy the public key to:

```
/home/ubuntu/.ssh/authorized_keys
```

on the **Managed Node**.

📌 This file allows the Control Node to connect without a password.

---

### ✅ Step 3: Test SSH Access

```bash
ssh ubuntu@192.168.1.10
```

✅ If no password is asked, the setup is successful.

---

## 📂 What Just Happened?

### ✔ Control Node:

* Public Key: `~/.ssh/id_rsa.pub`
* Private Key: `~/.ssh/id_rsa` (used to log in)

### ✔ Managed Node:

* File Updated: `~/.ssh/authorized_keys`
* It now **trusts** the Control Node’s public key

---

## 🛠️ Use With Ansible

Create an **inventory file** like this:

```ini
[web]
192.168.1.10

[web:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=~/.ssh/id_rsa
```

Run:

```bash
ansible web -m ping -i hosts.ini
```

✅ Ansible connects without password using the SSH key.

---

## 🧠 Final Summary

| Component      | Location                                                         |
| -------------- | ---------------------------------------------------------------- |
| Public Key     | Copied **from Control Node** → **to Managed Node**               |
| Authorized Key | Located in `/home/user/.ssh/authorized_keys` on **Managed Node** |
| Result         | Control Node can SSH into Managed Node without password          |

---

Would you like a playbook to automate this setup across multiple servers?
