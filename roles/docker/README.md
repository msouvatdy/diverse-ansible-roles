# How to use this docker role  ?

The purpose of this role is to install docker-ce on debian machine

## Variables

### Parameters

|                | Default value                         | Supported values                         |
|----------------|-------------------------------|-----------------------------|
| insecure_registry | `""` | your insecure registry           |

## Utilisation du role

Create a playbook and execute it. Example:

```bash
- hosts: my_servers
  become: true
  roles:
  - docker
```

`ansible-playbook myplaybook.yaml`
