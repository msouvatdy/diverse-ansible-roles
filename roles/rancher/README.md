# How to use this rancher role  ?

The purpose of this role is to install Rancher-ce on a Kubernetes cluster

## Prerequisite

You will need to install multiple ansible collection and python package in order to use this role

## Variables

### Parameters

|                | Default value                         | Supported values                         |
|----------------|-------------------------------|-----------------------------|
| kubeconfig | `"/home/vagrant/.kube/config"` | The path absolute path to your kubeconfig file           |

## Use the rancher role

Create a playbook and execute it. Example:

```bash
- hosts: my_servers
  become: true
  roles:
  - rancher
```

`ansible-playbook myplaybook.yaml`
