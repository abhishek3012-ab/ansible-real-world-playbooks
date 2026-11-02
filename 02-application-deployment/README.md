
# 02 - Automated Application Deployment

## Overview

This project automates the deployment of a Node.js application on Ubuntu servers using Ansible.

It installs application dependencies, clones the application from GitHub, configures a systemd service and manages the application automatically.

## Objectives

- Install Node.js, npm and Git.
- Clone application source code from GitHub.
- Install application dependencies.
- Configure a systemd service.
- Enable automatic application startup.
- Restart the application when service configuration changes.
- Verify application service status.

## Technologies

- Ansible
- Ubuntu Linux
- Node.js
- npm
- Git and GitHub
- systemd
- YAML
- AWS EC2

## Requirements

- Ansible control node.
- Ubuntu managed server.
- SSH connectivity.
- Sudo privileges.
- GitHub application repository.
- Valid package.json file with an npm start script.
- community.general Ansible collection.

## Files

- `main.yml` - Main Ansible playbook.

## Install Required Collection

```bash
ansible-galaxy collection install community.general
```

## Configuration

Update the following variables in `main.yml`:

- `app_repository` - GitHub application repository URL.
- `app_branch` - Application Git branch.
- `app_port` - Application port.

## Execution

Check server connectivity:

```bash
ansible appservers -i inventory.ini -m ansible.builtin.ping
```

Check playbook syntax:

```bash
ansible-playbook -i inventory.ini main.yml --syntax-check
```

Execute the playbook:

```bash
ansible-playbook -i inventory.ini main.yml
```

## Verification

Check application service:

```bash
sudo systemctl status myapp
```

Check application logs:

```bash
sudo journalctl -u myapp -f
```

Check application port:

```bash
curl http://localhost:3000
```

## Expected Result

- Node.js and npm should be installed.
- Application source code should be downloaded from GitHub.
- Application dependencies should be installed.
- A systemd service should be created and enabled.
- The Node.js application should start successfully.

## Real-World Use Case

Organisations use Ansible to automate application deployments across development, staging and production environments.

This reduces manual work and ensures consistent application configuration across multiple servers.

## Security Considerations

- Use a dedicated non-root application user in production.
- Store sensitive configuration in Ansible Vault.
- Use SSH authentication securely.
- Avoid storing credentials in GitHub.
