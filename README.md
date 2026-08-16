# 🚀 Ansible Linux Server Automation

A practical Infrastructure Automation project built using **Ansible, Linux, SSH, YAML, and AWS EC2**.

This project demonstrates how Ansible can be used to manage multiple Linux servers from a centralized control node and automate repetitive server administration and configuration tasks.

The project includes automated Nginx installation and configuration, Linux user management, server information gathering, SSH-based communication, inventory management, variables, group variables, loops, conditions, facts, handlers, Jinja2 templates, and reusable Ansible roles.

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Project Objectives](#-project-objectives)
- [Architecture](#-architecture)
- [Technologies Used](#-technologies-used)
- [Infrastructure](#-infrastructure)
- [Project Structure](#-project-structure)
- [Ansible Configuration](#-ansible-configuration)
- [Inventory](#-inventory)
- [SSH Configuration](#-ssh-configuration)
- [Testing Connectivity](#-testing-connectivity)
- [Group Variables](#-group-variables)
- [Playbooks](#-playbooks)
- [Nginx Role](#-nginx-role)
- [Nginx Installation](#-nginx-installation)
- [Nginx Service Management](#-nginx-service-management)
- [Jinja2 Template](#-jinja2-template)
- [Handlers](#-handlers)
- [Variables](#-variables)
- [Loops](#-loops)
- [Conditions](#-conditions)
- [Ansible Facts](#-ansible-facts)
- [Linux User Management](#-linux-user-management)
- [Server Information](#-server-information)
- [Privilege Escalation](#-privilege-escalation)
- [Idempotency](#-idempotency)
- [Testing and Verification](#-testing-and-verification)
- [Complete Workflow](#-complete-workflow)
- [Security](#-security)
- [How to Run the Project](#-how-to-run-the-project)
- [Benefits](#-benefits)
- [Ansible Concepts Practiced](#-ansible-concepts-practiced)
- [Learning Outcomes](#-learning-outcomes)
- [Future Improvements](#-future-improvements)
- [Author](#-author)

---

# 📌 Project Overview

Managing multiple Linux servers manually can become repetitive, time-consuming, and error-prone.

For example, an administrator may need to connect to every server individually and perform tasks such as:

--- text
SSH into server
    ↓
Update packages
    ↓
Install Nginx
    ↓
Start Nginx
    ↓
Enable Nginx
    ↓
Create users
    ↓
Configure files
    ↓
Deploy web content
    ↓
Restart services

---

#🎯 Project Objectives

The main objectives of this project are:

Configure an Ansible control node.
Manage multiple Linux servers using Ansible.
Establish SSH-based communication with managed nodes.
Create and manage Ansible inventories.
Automate Linux server configuration.
Install and configure Nginx.
Start and enable Nginx services.
Deploy dynamic web pages using Jinja2.
Create Linux users automatically.
Assign sudo privileges to users.
Use Ansible variables.
Use group variables.
Use loops to reduce repetitive tasks.
Use conditions for OS-specific automation.
Gather and use Ansible facts.
Implement handlers.
Create reusable Ansible roles.
Practice idempotent infrastructure automation.
Manage AWS EC2 Linux servers through Ansible.

---

 🏗️ Architecture

The project uses one EC2 instance as the Ansible Control Node and multiple EC2 instances as Managed Nodes.

                         AWS CLOUD
                            |
                            |
                       AWS VPC
                            |
                            |
                +------------------------+
                |   Ansible Controller   |
                |                        |
                |   Ubuntu Linux         |
                |   Ansible              |
                |   SSH Client           |
                +-----------+------------+
                            |
                            |
                         SSH
                     /      |      \
                    /       |       \
                   /        |        \
                  ▼         ▼         ▼
          +------------+ +------------+
          | Web Server | | Web Server |
          |     1      | |     2      |
          |            | |            |
          | Ubuntu     | | Ubuntu     |
          | Nginx      | | Nginx      |
          | Managed    | | Managed    |
          | Node       | | Node       |
          +------------+ +------------+
 
  🔄 Communication Flow
  
   Administrator
       |
       ▼
  Ansible Control Node
      |
      | SSH
      |
      +--------------------+
      |                    |
      ▼                    ▼
 Managed Node 1       Managed Node 2
      |                    |
      ▼                    ▼
   Nginx                Nginx
   Users                Users
   Config               Config
   Facts                Facts
---       

  🛠️ Technologies Used
  
Technology	Purpose
Ansible	Infrastructure automation
Linux	Server operating system
Ubuntu	Control and managed nodes
AWS EC2	Cloud infrastructure
SSH	Secure communication
YAML	Playbooks and configuration
Jinja2	Dynamic templates
Nginx	Web server
Git	Version control
GitHub	Source code repository

---

☁️ Infrastructure

The project was implemented using multiple AWS EC2 instances.

Ansible Control Node
Operating System: Ubuntu 24.04 LTS
Role: Ansible Control Node

The control node is responsible for:

Running Ansible.
Maintaining the inventory.
Executing playbooks.
Connecting to managed servers.
Applying configurations.
Collecting server information.
Managed Nodes

The managed nodes are Ubuntu Linux EC2 instances.

Their responsibilities include:

Running Nginx.
Receiving Ansible configuration.
Creating Linux users.
Serving the generated web page.
Providing system information through Ansible facts.

The actual private IP addresses are intentionally not documented here. When reproducing this project, use the private IP addresses of your own EC2 instances.

---

📂 Project Structure

ansible-linux-automation/
│
├── README.md
├── .gitignore
├── ansible.cfg
│
├── inventory/
│   │
│   ├── hosts
│   │
│   └── group_vars/
│       └── web.yml
│
├── playbooks/
│   │
│   ├── setup.yml
│   ├── users.yml
│   └── server-info.yml
│
└── roles/
    │
    └── nginx/
        │
        ├── defaults/
        │   └── main.yml
        │
        ├── handlers/
        │   └── main.yml
        │
        ├── tasks/
        │   └── main.yml
        │
        └── templates/
            └── index.html.j2

---

📁 Directory Explanation

ansible.cfg

Project-level Ansible configuration.

inventory/

Contains the Ansible inventory and group variables.

inventory/hosts

Contains the managed server definitions.

inventory/group_vars/

Contains variables that apply to a particular inventory group.

playbooks/

Contains the main Ansible automation playbooks.

roles/

Contains reusable Ansible roles.

roles/nginx/

Contains all Nginx-related automation.
----

🧠 Ansible Concepts Practiced

This project provides practical experience with:

Ansible
│
├── Control Node
├── Managed Nodes
├── SSH
├── Inventory
├── Inventory Groups
├── Playbooks
├── YAML
├── Modules
├── Variables
├── Group Variables
├── Loops
├── Conditions
├── Facts
├── Jinja2 Templates
├── Handlers
├── Roles
├── Defaults
├── Privilege Escalation
└── Idempotency

---
📚 Ansible Modules Used

Module	Purpose
ping	Test Ansible connectivity
apt	Install and manage Ubuntu packages
service	Manage Linux services
user	Create and manage Linux users
template	Deploy Jinja2 templates
debug	Display variables and information
setup	Gather system facts
