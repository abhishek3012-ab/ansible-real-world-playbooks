
# 03 - Linux Server Security Hardening

## Overview

This project automates important Linux server security configurations using Ansible.

It manages Linux users, configures SSH security, installs firewall packages, applies firewall rules and updates installed packages.

## Objectives

- Update installed Ubuntu packages.
- Install UFW firewall and OpenSSH server.
- Create a dedicated deployment user.
- Configure SSH public key authentication.
- Disable direct root SSH login.
- Allow SSH, HTTP and HTTPS traffic.
- Enable UFW firewall.
- Verify firewall configuration.

## Technologies

- Ansible
- Ubuntu Linux
- SSH
- UFW Firewall
- YAML
- Linux User Management
- AWS EC2

## Requirements

- Ansible control node.
- Ubuntu managed server.
- SSH connectivity.
- Sudo privileges.
- Valid SSH public key.
- community.general Ansible collection.

## Files

- `main.yml` - Main Ansible playbook.

## Install Required Collection

```bash
ansible-galaxy collection install community.general
```

## Configuration

Configure the following variables in `main.yml`:

- `security_user` - Name of the deployment user.
- `security_ssh_port` - SSH port number.
- `security_ssh_public_key` - SSH public key of the deployment user.

Provide the public key using a secure variable or Ansible Vault.

## Execution

Check server connectivity:

```bash
ansible all -i inventory.ini -m ansible.builtin.ping
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

Check firewall status:

```bash
sudo ufw status verbose
```

Check SSH service:

```bash
sudo systemctl status ssh
```

Check deployment user:

```bash
id deployuser
```

Check SSH configuration:

```bash
sudo sshd -T | grep permitrootlogin
```

Expected output:

```text
permitrootlogin no
```

## Expected Result

- Ubuntu packages should be updated.
- A dedicated deployment user should be created.
- SSH public key authentication should be configured when a key is supplied.
- Root SSH login should be disabled.
- UFW firewall should be enabled.
- SSH, HTTP and HTTPS traffic should be allowed.

## Real-World Use Case

Organisations use security automation to apply consistent security configurations across multiple Linux servers.

This helps reduce manual configuration errors and improves server security.

## Security Considerations

- Keep an existing SSH session open while testing new SSH access.
- Allow SSH in AWS Security Groups before enabling firewall restrictions.
- Verify the deployment user's access before disabling root login.
- Test security changes on non-production servers first.
- Use Ansible Vault for sensitive information.

