# How to use this nfs role ?

The purpose of this role is to install NFS server on a Debian 11.

## Variables

### Variable used by this role

|                | Default value                        | Supported values                         |
|----------------|-------------------------------|-----------------------------|
| mount_path | `/data/k8s` | your absolute path of your nfs server|
| exposed_network | `10.10.20.0/24` | your cidr |

## Use the role

Create a playbook that call the nfs role. Example:

```bash
- hosts: my_servers
  become: true
  roles:
  - nfs
```

`ansible-playbook myplaybook.yaml`
