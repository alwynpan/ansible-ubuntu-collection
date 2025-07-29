# Ansible Collection - alwynpan.ubuntu

A comprehensive Ansible collection for Ubuntu system configuration, automation, and DevOps workflows. This collection provides roles for common system setup, Docker installation, HAProxy reverse proxy with Let's Encrypt SSL, XFS volume management, package management, NTP, timezone, AWS CLI, and more.

## Features & Included Roles

- **ubuntu_common**: Common Ubuntu system configuration and package management
- **ubuntu_docker**: Install and configure Docker Engine and tools
- **ubuntu_haproxy_certbot**: Install and configure HAProxy with Certbot and Let's Encrypt SSL
- **ubuntu_volume_xfs**: Manage and automate XFS volume creation, formatting, and mounting

## Requirements

- Ubuntu 18.04 or later
- Ansible 2.9 or later
- Internet connectivity for package and repository access

## Installation

Install the collection from Ansible Galaxy:

```bash
ansible-galaxy collection install alwynpan.ubuntu
```

## Usage

Example playbook using all roles:

```yaml
- hosts: all
  become: true
  roles:
    - alwynpan.ubuntu_common
    - alwynpan.ubuntu_docker
    - alwynpan.ubuntu_haproxy_certbot
    - alwynpan.ubuntu_volume_xfs
```

You can also use roles individually and pass variables as needed. See each role's README for details:

- [ubuntu_common](roles/ubuntu_common/README.md)
- [ubuntu_docker](roles/ubuntu_docker/README.md)
- [ubuntu_haproxy_certbot](roles/ubuntu_haproxy_certbot/README.md)
- [ubuntu_volume_xfs](roles/ubuntu_volume_xfs/README.md)

## License

MIT-0

## Author Information

- **Author**: Alwyn Pan
- **GitHub**: https://github.com/alwynpan/ansible-ubuntu-collection
- **Issues**: https://github.com/alwynpan/ansible-ubuntu-collection/issues
