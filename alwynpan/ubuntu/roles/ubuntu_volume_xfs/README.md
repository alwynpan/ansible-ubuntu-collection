Ubuntu Volume XFS
=================

This role manages and formats XFS volumes on Ubuntu systems. It can be used to automate the creation, formatting, and mounting of XFS filesystems for persistent storage.

Requirements
------------

- Ubuntu 18.04 or later
- Ansible 2.9 or later

Role Variables
--------------

This role uses a nested variable structure to support multiple instances and multiple volumes per instance. The main variable is `instances`, which is a list of instance definitions. Each instance can have a list of `volumes` to be managed.

### Structure

- `instances`: List of instance objects.
  - `name`: (string) Name of the instance (for identification/documentation).
  - `volumes`: List of volume objects for the instance.
    - `vol_name_prefix`: (string) Prefix for the logical volume name (e.g., 'docker', 'data').
    - `vol_size`: (integer) Size of the volume in GB.
    - `device`: (string) The device to use (e.g., `/dev/vdb`).
    - `mountpoint`: (string) The directory where the volume will be mounted (e.g., `/var/lib/docker`).

### Example variable usage

```yaml
instances:
  - name: instance1
    volumes:
      - vol_name_prefix: docker
        vol_size: 25
        device: /dev/vdb
        mountpoint: /var/lib/docker
      - vol_name_prefix: data
        vol_size: 50
        device: /dev/vdc
        mountpoint: /data
```

Dependencies
------------

This role has no external dependencies.

What This Role Does
-------------------

1. **Installs XFS utilities**: Ensures `xfsprogs` is present.
2. **Creates and formats XFS filesystem**: Formats the specified device as XFS (if not already formatted).
3. **Creates mount point**: Ensures the mount directory exists.
4. **Mounts the filesystem**: Mounts the device at the specified mount point with the given options.
5. **Configures fstab**: Ensures the mount persists across reboots.

Example Playbook
----------------

```yaml
- hosts: storage_servers
  become: true
  vars:
    instances:
      - name: instance1
        volumes:
          - vol_name_prefix: docker
            vol_size: 25
            device: /dev/vdb
            mountpoint: /var/lib/docker
          - vol_name_prefix: data
            vol_size: 50
            device: /dev/vdc
            mountpoint: /data
  roles:
    - alwynpan.ubuntu_volume_xfs
```

License
-------

MIT-0

Author Information
------------------

- **Author**: Alwyn Pan
- **GitHub**: https://github.com/alwynpan/ansible-ubuntu-collection
- **Issues**: https://github.com/alwynpan/ansible-ubuntu-collection/issues
