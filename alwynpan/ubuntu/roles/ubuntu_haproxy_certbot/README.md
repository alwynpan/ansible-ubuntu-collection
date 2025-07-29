Ubuntu HAProxy Certbot
=====================

This role installs and configures HAProxy and Certbot on Ubuntu systems. It sets up a secure reverse proxy with automated SSL certificate management using Let's Encrypt.

Requirements
------------

- Ubuntu 18.04 or later
- Ansible 2.9 or later

Role Variables
--------------

The following variables can be customized in your playbook or inventory:

- `haproxy_version`: The version of HAProxy to install (e.g., `3.2`).
- `letsencrypt_haproxy_cert_dir`: Directory to store Let's Encrypt certificates and DH parameters (e.g., `/etc/letsencrypt/live/example.com`).

Example variable usage:

```yaml
haproxy_version: "3.2"
letsencrypt_haproxy_cert_dir: "/etc/letsencrypt/live/example.com"
```

Dependencies
------------

This role has no external dependencies.

What This Role Does
-------------------

1. **Adds HAProxy PPA**: Adds the official HAProxy repository for the specified version.
2. **Installs HAProxy**: Installs the specified version of HAProxy.
3. **Installs Certbot**: Installs Certbot via snap for Let's Encrypt certificate management.
4. **Creates DH Parameters**: Downloads strong Diffie-Hellman parameters for SSL security.
5. **Configures HAProxy**: Deploys a template configuration for HAProxy to work with Let's Encrypt and SSL.
6. **Restarts HAProxy**: Notifies the handler to restart HAProxy after configuration changes.

Example Playbook
----------------

```yaml
- hosts: haproxy_servers
  become: true
  vars:
    haproxy_version: "3.2"
    letsencrypt_haproxy_cert_dir: "/etc/letsencrypt/live/example.com"
  roles:
    - alwynpan.ubuntu_haproxy_certbot
```

License
-------

MIT-0

Author Information
------------------

- **Author**: Alwyn Pan
- **GitHub**: https://github.com/alwynpan/ansible-ubuntu-collection
- **Issues**: https://github.com/alwynpan/ansible-ubuntu-collection/issues
