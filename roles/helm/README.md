# Comment utiliser le role helm ?

Ce roles a pour but d'installer le binaire Helm sur des machines de type linux.


# Variables
Les variables utilisées dans ce projet sont:
|                |Valeur par défaut                          |Valeurs supportées                         |
|----------------|-------------------------------|-----------------------------|
|helm_version|	`v3.11.1` |version de helm disponible sur https://github.com/helm/helm/tree/main            |
|os_type          |`linux`            |linux and darwin           |
|architecture_type          |`amd64`|amd64, arm64, arm, 386, ppc64le, s390x|

# Utilisation du roles

Créer un playbook appelant le roles et l'exécuter. Exemple:
```bash
- hosts: my-server
  become: true
  roles:
  - helm
```

## Mise à jour de Helm

Le roles dispose d'un tag upgrade_helm permettant de réinstaller Helm.
`ansible-playbook myplaybook.yaml -t upgrade_helm`

## Désinstallation de Helm

Le roles dispose d'un tag permettant la désinstallation de Helm. (Suppression du binaire se situant dans /usr/local/bin/helm)

`ansible-playbook myplaybook.yaml -t uninstall_helm`
