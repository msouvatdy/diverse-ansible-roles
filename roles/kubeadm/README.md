# Comment utiliser le role kubeadm ?

Ce roles a pour but d'installer kubeadm sur des machines de type linux.

# Variables

## Les variables utilisées dans ce projet pour personnaliser son installation sont:
|                |Valeur par défaut                          |Valeurs supportées                         |
|----------------|-------------------------------|-----------------------------|
|containerd_version|	`1.6.18` |version de containerd disponible sur https://github.com/containerd/containerd/releases           |
|architecture| `amd64` | amd64, arm64|
|os        |`linux`            |linux et            |
|version_runc| `v1.1.4` |version de runc disponible sur https://github.com/opencontainers/runc/releases |
|kubelet_ver - kubectl_ver - kubeadm_ver | `1.26.1-00`| version disponible https://kubernetes.io/releases/|

## Autre variables


|                |Valeur par défaut                          | Info                     |
|----------------|-------------------------------|-----------------------------|
|containerd_service| `https://raw.githubusercontent.com/containerd/containerd/main/containerd.service` | permet de créer le service containerd|
|key        |`https://packages.cloud.google.com/apt/doc/apt-key.gpg`            | permet d'ajouter le repo apt de google            |

# Utilisation du role

Créer un playbook appelant le role à exécuter. Exemple:
```bash
- hosts: my_servers
  become: true
  roles:
  - kubeadm
```
`ansible-playbook myplaybook.yaml`