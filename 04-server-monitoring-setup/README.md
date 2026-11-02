
# 04 - Automated Server Monitoring Setup

## Overview

This project automates the installation and configuration of Prometheus Node Exporter on Ubuntu servers using Ansible.

Node Exporter collects Linux server metrics such as CPU usage, memory usage, filesystem information and system activity.

It exposes these metrics through an HTTP endpoint for Prometheus to collect.

## Objectives

- Update Ubuntu package cache.
- Install Prometheus Node Exporter.
- Configure Node Exporter service.
- Enable automatic service startup.
- Start the monitoring service.
- Verify monitoring service status.
- Check the metrics endpoint.

## Technologies

- Ansible
- Ubuntu Linux
- Prometheus Node Exporter
- Linux
- YAML
- systemd
- AWS EC2

## Requirements

- Ansible control node.
- Ubuntu managed server.
- SSH connectivity.
- Sudo privileges.
- Network access for package installation.

## Files

- `main.yml` - Main Ansible playbook.

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

Check Node Exporter service:

```bash
sudo systemctl status prometheus-node-exporter
```

Check whether port 9100 is listening:

```bash
sudo ss -tulnp | grep 9100
```

Check metrics endpoint:

```bash
curl http://localhost:9100/metrics
```

You should see Prometheus-formatted system metrics.

## Expected Result

- Node Exporter should be installed.
- Monitoring service should be running.
- Service should start automatically after reboot.
- Metrics should be available through port 9100.

## Real-World Use Case

Organisations use Node Exporter to monitor Linux servers across their infrastructure.

A central Prometheus server can collect these metrics and Grafana can display them through monitoring dashboards.

## Security Considerations

- Do not expose port 9100 publicly.
- Allow access only from trusted monitoring servers.
- Use private networking where possible.
- Configure appropriate firewall rules.

## Important Note

This project installs Node Exporter only.

Prometheus server installation, Prometheus scrape configuration and Grafana dashboard setup are separate monitoring tasks.
