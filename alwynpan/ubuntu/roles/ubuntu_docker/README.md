Ubuntu Docker
=============

This role installs and configures Docker on Ubuntu systems. It handles the removal of old Docker versions, installs all required dependencies, adds Docker's official GPG key and repository, and installs the latest Docker Engine and related tools.

Requirements
------------

- Ubuntu 18.04 or later
- Ansible 2.9 or later

Role Variables
--------------

This role does not require any variables by default. All configuration is handled internally for a standard Docker installation. You may override variables in your playbook or inventory if you wish to customize the installation (e.g., using a different Docker repository or version).

Dependencies
------------

This role has no external dependencies.

What This Role Does
-------------------

1. **Removes old Docker versions**: Uninstalls any existing Docker, Podman, or related packages that may conflict with the new installation.
2. **Installs dependencies**: Installs required system packages for Docker installation (curl, ca-certificates, gnupg, etc.).
3. **Adds Docker GPG key**: Downloads and installs Docker's official GPG key for package verification.
4. **Adds Docker repository**: Adds the official Docker APT repository for Ubuntu.
5. **Installs Docker Engine and tools**: Installs the latest versions of Docker Engine, CLI, Buildx, Compose plugin, and containerd.

Example Playbook
----------------

Basic usage:

```yaml
- hosts: ubuntu_servers
  become: true
  roles:
    - alwynpan.ubuntu_docker
```

License
-------

MIT-0

Author Information
------------------

- **Author**: Alwyn Pan
- **GitHub**: https://github.com/alwynpan/ansible-ubuntu-collection
- **Issues**: https://github.com/alwynpan/ansible-ubuntu-collection/issues
