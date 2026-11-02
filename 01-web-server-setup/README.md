
# 01 - Automated Web Server Setup

## Overview

This project automates the installation and configuration of Nginx web servers using Ansible.

## Objectives

- Install Nginx on Ubuntu servers.
- Deploy website homepage.
- Configure Nginx service.
- Automatically restart Nginx when website configuration changes.
- Verify service status.

## Technologies

- Ansible
- Ubuntu Linux
- Nginx
- YAML
- AWS EC2

## Requirements

- Ansible control node.
- Ubuntu managed server.
- SSH connectivity.
- Sudo privileges.

## Files

- `main.yml` - Main Ansible playbook.

## Execution

Check connectivity:

```bash
ansible webservers -i inventory.ini -m ansible.builtin.ping
```

Check syntax:

```bash
ansible-playbook -i inventory.ini main.yml --syntax-check
```

Execute:

```bash
ansible-playbook -i inventory.ini main.yml
```

## Verification

Check Nginx:

```bash
sudo systemctl status nginx
```

Check website:

```bash
curl http://SERVER-IP
```

## Expected Result

Nginx should be installed, enabled and running. The deployed homepage should be accessible through the server IP.
