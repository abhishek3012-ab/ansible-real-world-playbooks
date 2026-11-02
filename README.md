
# Ansible Real-World Playbooks

A collection of practical Ansible playbooks for automating Linux server administration and DevOps operations.

## Projects

| No.| Project                       | Description                                              |
|----|-------------------------------|----------------------------------------------------------|
| 01 | Web Server Setup              | Automated Nginx installation and configuration           |
| 02 | Application Deployment        | Deploy Node.js applications using Git and systemd        |
| 03 | Linux Security Hardening      | SSH security, user management and firewall configuration |
| 04 | Server Monitoring Setup       | Install and configure Prometheus Node Exporter           |
| 05 | Automated Backup and Recovery | Schedule automated Linux configuration backups           |

## Technologies Used

- Ansible
- YAML
- Linux / Ubuntu
- AWS EC2
- Nginx
- Node.js
- Prometheus Node Exporter
- Bash Scripting
- Git and GitHub

## Repository Structure

```text
ansible-real-world-playbooks/
├── 01-web-server-setup/
├── 02-application-deployment/
├── 03-linux-security-hardening/
├── 04-server-monitoring-setup/
├── 05-automated-backup-recovery/
├── .gitignore
└── README.md
```

Each project contains:
- `main.yml` - Ansible playbook
- `README.md` - Project documentation and execution instructions

## Prerequisites

- Ansible installed on the control node.
- Ubuntu Linux managed servers.
- SSH connectivity between control node and managed servers.
- Appropriate SSH permissions.
- Python installed on managed nodes.
- Required Ansible collections installed.

## Basic Commands

Check Ansible version:

```bash
ansible --version
```

Check connectivity:

```bash
ansible all -i inventory.ini -m ansible.builtin.ping
```

Check playbook syntax:

```bash
ansible-playbook -i inventory.ini main.yml --syntax-check
```

Run a playbook:

```bash
ansible-playbook -i inventory.ini main.yml
```

Run in check mode:

```bash
ansible-playbook -i inventory.ini main.yml --check
```

## Important Security Notice

- Never upload SSH private keys or passwords.
- Use Ansible Vault for sensitive variables.
- Test playbooks in a development environment before production use.
- Review firewall and SSH configurations before applying changes.

## Learning Objectives

This repository demonstrates practical experience with:

- Configuration management
- Infrastructure automation
- Linux administration
- Application deployment
- Server security
- Monitoring
- Backup automation

## Author

Abhishek Birajdar

GitHub: https://github.com/abhishek3012-ab

---

This repository is created for learning, practical implementation and DevOps portfolio development.
