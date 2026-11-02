
# 05 - Automated Backup and Recovery

## Overview

This project automates Linux server configuration backups using Ansible and Bash scripting.

It creates backup directories, generates a backup script, compresses important configuration files and schedules daily backups using cron.

It also removes old backup files according to the configured retention period.

## Objectives

- Create a dedicated backup directory.
- Install required backup utilities.
- Generate an automated Bash backup script.
- Compress Linux configuration files.
- Schedule daily backups using cron.
- Configure backup retention.
- Verify backup script configuration.

## Technologies

- Ansible
- Ubuntu Linux
- Bash Scripting
- Cron
- Tar
- YAML
- AWS EC2

## Requirements

- Ansible control node.
- Ubuntu managed server.
- SSH connectivity.
- Sudo privileges.
- Required disk space for backups.

## Files

- `main.yml` - Main Ansible playbook.

## Configuration

Configure the following variables in `main.yml`:

- `backup_source` - Directory to back up.
- `backup_directory` - Destination for backup files.
- `backup_script` - Location of the backup script.
- `backup_retention_days` - Number of days for backup retention.

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

Check backup directory:

```bash
sudo ls -lh /var/backups/server
```

Check backup script:

```bash
sudo ls -l /usr/local/bin/server-backup.sh
```

Check scheduled cron job:

```bash
sudo crontab -l
```

Execute backup manually:

```bash
sudo /usr/local/bin/server-backup.sh
```

Check generated backup files:

```bash
sudo ls -lh /var/backups/server/
```

Verify backup archive:

```bash
sudo tar -tzf /var/backups/server/backup-file-name.tar.gz
```

Replace `backup-file-name.tar.gz` with the actual generated backup filename.

## Expected Result

- Backup directory should be created.
- Bash backup script should be generated.
- Linux configuration files should be compressed.
- Daily cron job should be configured for 2:00 AM.
- Old backup files should be removed according to the retention policy.

## Real-World Use Case

Organisations use automated backup systems to protect important server configuration files and support disaster recovery operations.

Automated backups reduce manual work and help maintain regular backup schedules.

## Security Considerations

- Store backups in secure locations.
- Restrict access to backup directories.
- Encrypt sensitive backup files.
- Keep additional copies outside the source server.
- Regularly test backup restoration.
- Never store sensitive backup data in public GitHub repositories.

## Important Note

This project demonstrates configuration-file backup automation.

For production environments, extend the solution with remote backup storage, encryption, backup integrity checks and tested restoration procedures.

