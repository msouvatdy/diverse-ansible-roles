# How to use this gitlab role  ?

The purpose of this role is to install Gitlab-ce on a Kubernetes cluster or on a Debian 11 server

## Prerequisite

You need to have a Kubernetes cluster or a Debian 11 server in order to install

## Variables

### Parameters

|                | Default value                         | Supported values                         |
|----------------|-------------------------------|-----------------------------|
| type_of_install | `package` | package or k8s           |
| external_url | `super-gitlab.io` | url for your gitlab |
| private_cert.use_private_cert | `no` | If you want to use your own certificate replace this variable to yes|
| key_path and crt_path | `/path_to_cert` | provide path to your certificate |

## Use the gitlab role

Create a playbook and execute it. Example:
> Note: You need to install helm in order to use this role

```bash
- hosts: my_servers
  become: true
  roles:
  - gitlab
```

`ansible-playbook myplaybook.yaml`
