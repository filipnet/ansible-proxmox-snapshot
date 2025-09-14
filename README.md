![Ansible Compatible](https://img.shields.io/badge/Ansible-compatible-green)
![Proxmox API Compatible](https://img.shields.io/badge/Proxmox_API-compatible-green)

# Ansible Role: proxmox-snapshot

> ℹ️ **Note**  
> A detailed tutorial is available on my blog: [www.filipnet.de/ansible-proxmox-snapshot](https://www.filipnet.de/ansible-proxmox-snapshot)

This Ansible role creates **pre-update snapshots** for Proxmox QEMU VMs or LXC containers.

## Table of contents

<!-- TOC -->

- [Ansible Role: proxmox-snapshot](#ansible-role-proxmox-snapshot)
  - [Table of contents](#table-of-contents)
  - [Requirements](#requirements)
  - [Features](#features)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [Contributions](#contributions)
  - [License](#license)

<!-- /TOC -->

## Requirements

- Ansible 2.9 or higher
- Proxmox API access (host and API token)

## Features

- **Native Ansible role** built directly on the **Proxmox API**
- Automatic detection of the correct **ID** from the **hostname**
- Internal resolution of the **node** without manual steps
- **No manual input** required
- **No extra software** dependencies
- Works without **cluster-specific hacks**
- Seamlessly integrates with your **Ansible playbooks**

## Role Variables

Variables can be set in `defaults/main.yml`.  
**Recommended:** Define them in `group_vars/all.yml` or a group-specific vars file.  
Setting them per host is possible but not efficient, as it would require repeating values on every system to be updated.

## Example Playbook

Create a playbook `snapshot.yml`:

```yaml
- hosts: proxmox_vms
  roles:
    - role: proxmox-snapshot
      vars:
        proxmox_snapshot_host: "pvenode.examplecorp.com"
        proxmox_snapshot_api_token: "ansible@pve!token-ansible=12345678-ABCD-1234-ABCD-1234567890AB"
```

Run the role against an inventory and limit to a specific host:

```bash
ansible-playbook -i inventory/examplecorp.com snapshot.yml -l host01.examplecorp.com
```

## Contributions

Contributions are welcome! If you would like to improve this project, please feel free to submit a pull request. All contributions, bug reports, and feature suggestions are appreciated.

## License

`proxmox-snapshot` and all individual scripts are under the **BSD 3-Clause license** unless explicitly noted otherwise. See the [LICENSE](./LICENSE) file for more details.
