Ubuntu Common
============

This role provides common Ubuntu system configuration and package management functionality. It handles basic system setup including package updates, dependency installation, timezone configuration, NTP synchronization, and AWS CLI installation.

Requirements
------------

- Ubuntu 18.04 or later
- Ansible 2.9 or later

Role Variables
--------------

### Default Variables

The following variables can be customized in your playbook or inventory:

- `instances`: List of instances with timezone configuration
  - `timezone`: Timezone to set (default: 'Etc/UTC')

### Example Variable Usage

```yaml
instances:
  - name: instance1
    timezone: 'Australia/Melbourne'
  - name: instance2
    timezone: 'America/New_York'
```

Dependencies
------------

This role has no external dependencies.

What This Role Does
-------------------

1. **System Updates**: Upgrades all packages to their latest versions
2. **Package Installation**: Installs essential system packages including:
   - Build tools (build-essential, python3-dev)
   - Development tools (git, curl, vim)
   - System utilities (lvm2, snapd, unzip)
   - Python tools (python3-pip, python3-virtualenv, pipx)
   - AWS CLI via snap

3. **Timezone Configuration**: Sets system timezone (default: UTC)
4. **NTP Configuration**: 
   - Configures systemd-timesyncd with University of Melbourne NTP servers
   - Ensures RTC is maintained in UTC
   - Restarts timesyncd service

5. **AWS CLI Installation**: Installs AWS CLI v2 via snap

Example Playbook
----------------

```yaml
- hosts: ubuntu_servers
  vars:
    instances:
      - name: instance1
        timezone: 'Australia/Melbourne'
  roles:
    - alwynpan.ubuntu.ubuntu_common
```

License
-------

MIT-0

Author Information
------------------

- **Author**: Alwyn Pan
- **GitHub**: https://github.com/alwynpan/ansible-ubuntu-collection
- **Issues**: https://github.com/alwynpan/ansible-ubuntu-collection/issues
