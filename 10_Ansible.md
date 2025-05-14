## 1. What is configuration management system?
-  Imagine you have a computer lab with 100 computers, and you need to install the same software, settings, and updates on all of them. 
- Doing it manually would be time-consuming and error-prone.

- Instead, Configuration Management helps automate this process using tools like Ansible, Puppet, Chef, or Terraform, ensuring that all systems are set up correctly and remain consistent.

## 2. What is ansible playbook in simple words?
- An Ansible Playbook is a file (written in YAML) that contains a set of instructions (tasks) to automate processes like configuring servers, deploying applications, or managing systems.

- Think of it like a to-do list for Ansible, where you define step-by-step what needs to be done on one or more machines.

## 3. How to use ansible?
- Ansible works by installing it on a control machine (your computer or server) and then using it to manage remote machines. You define what needs to be done in a Playbook (a YAML file), and Ansible executes it on the target machines. It uses SSH (for Linux) and WinRM (for Windows) to connect to them.

## 4. Does ansible support Linux and windows or only Linux?

- support both, for Linux it use protocol called ```ssh``` and for windows it use protocol ``` WinRM``` (Windows Remote Management). 

## 5. Difference between puppet and ansible, chef and ansible?
## Comparison: Ansible vs Puppet vs Chef

| Feature         | Ansible           | Puppet               | Chef                 |
|---------------|-----------------|------------------|------------------|
| **Setup**     | Easy (agentless) | Needs agent      | Needs agent      |
| **Language**  | YAML             | Custom DSL (Puppet Language) | Ruby |
| **Communication** | Push-based    | Pull-based       | Pull-based       |
| **Ease of Use** | Simple, human-readable | Moderate | Complex |
| **Best for**   | Quick deployments, automation | Large enterprise setups | Infrastructure as code |



## 6. Why you choose ansible over the other configuration management tools? 
- Agentless – No need to install extra software on managed machines.
- Simple syntax – Uses easy-to-read YAML.
- Faster setup – No complicated infrastructure required.
- Push-based model – Changes are immediately applied.

## 7. Which mechanism is ansible? push or pull, and explain why? 
- Ansible uses a push-based mechanism.

    - The control machine pushes the configuration to target servers, meaning no need for clients to pull updates.
    - This makes deployments faster and easier to manage.

## 8. what programming language that ansible uses? 
- Ansible uses YAML for writing playbooks and configurations.

## 9. Does ansible supports all the cloud provider or not?
- Yes, Ansible supports all major cloud providers, including AWS, Azure, Google Cloud, and more. 
- You can use Ansible modules to automate cloud tasks.

## 10. What is difference between ansible adhoc commands and ansible playbook?

## Ansible: Ad-hoc Command vs Playbook

| Feature       | Ad-hoc Command            | Playbook                        |
|--------------|---------------------------|---------------------------------|
| **Definition** | One-time command          | Structured automation           |
| **Usage**     | Quick tasks (e.g., restart service) | Complex configurations |
| **Example**   | `ansible all -m ping`     | `ansible-playbook my-playbook.yml` |


## 11. How  do you group servers in ansible or how can you execute certain number of tasks only on certain number of virtual machines for ansible?

-  Grouping Servers in Ansible You use an **inventory file** to group servers.

- Example Inventory File:
```ini
[web_servers]
server1
server2

[db_servers]
db1
db2
```

- Ansible Playbook Example

Below is an example of an Ansible Playbook that installs Apache on web servers:

```yaml
- hosts: web_servers
  tasks:
    - name: Install Apache
      yum:
        name: httpd
        state: present
```

## 12. What is ansible roles?
- Ansible roles help organize large playbooks by breaking them into reusable components.
- Each role has separate tasks, variables, handlers, and templates.


# AV git repo for sample playbook:-
https://github.com/ansible/ansible-examples

- recommended e.g. in repo ```jboss-standalone```
