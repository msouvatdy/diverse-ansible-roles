# How to use this rancher role  ?

The purpose of this role is to install Rancher-ce on a Kubernetes cluster

## Prerequisite

You will need to install multiple ansible collection and python package in order to use this role

```bash
ansible-galaxy collection install kubernetes.core
sudo apt install python3-pip -y
sudo pip install kubernetes>=12.0.0
sudo pip install PyYAML>=3.11
sudo pip install jsonpatch
```

## Variables

### Parameters

|                | Default value                         | Supported values                         |
|----------------|-------------------------------|-----------------------------|
| kubeconfig | `"/home/vagrant/.kube/config"` | The path absolute path to your kubeconfig file           |
| hostname_ingress | `superrancher.io` | hostname for your ingress |
| cert_manager_version | `v1.7.1` | version of the cert_manager |
| rancher_version | `v2.7.1` | version of rancher |
| privateCA | `false` | true or false |
| ingress_tls | `false` | true or false |
| default_password | `Aqwzsxedc@01` | the default password for rancher |

## Use the rancher role

Create a playbook and execute it. Example:
> Note: You need to install helm in order to use this role

```bash
- hosts: my_servers
  become: true
  roles:
  - helm
  - rancher
```

`ansible-playbook myplaybook.yaml`

## Test install with your own SSL certificates

This is how I tested the certificate on Rancher

### Generate CA (optionnal)

```bash
openssl req -x509 -newkey rsa:4096 -days 365 -nodes -keyout ca-key.pem -out cacerts.pem -subj "/C=FR/ST=Ile de France/L=Paris/O=Super Company/OU=Super Test/CN=*.superrancher.io/emailAddress=super.example@example.com"
```

|                | Default value                         | Purpose                        |
|----------------|-------------------------------|-----------------------------|
| C | FR | Country|
|ST | Ile de France |  State or province |
| L | Paris | City |
| O | Super Company | Organisation |
| OU | Super Test | Organisation Unit |
|CN | *.superrrancher.io | Common Name or domain name |
|emailAddress |super.example@example.com | address|

### Generate web server's private key and certificate signing request (CSR) (optional)

```bash
openssl req -newkey rsa:4096 -nodes -keyout tls.key -out tls.req -subj "/C=FR/ST=Ile de France/L=Paris/O=Super Company/OU=Super Rancher/CN=*.superrancher.io/emailAddress=super@example.com"
```

### Use CA's private key to sign web server's CSR and get back the signed certificate (optional)

```bash
openssl x509 -req -in tls.req -days 60 -CA cacerts.pem -CAkey ca-key.pem -CAcreateserial -out tls.crt
```

To verify if your certificate is correct:

`openssl verify -CAfile cacerts.pem tls.crt`

### Create secret for rancher (mandatory)

Documentation on how to install rancher with ssl: <https://ranchermanager.docs.rancher.com/pages-for-subheaders/install-upgrade-on-a-kubernetes-cluster>

```bash
kubectl create ns cattle-system

kubectl -n cattle-system create secret tls tls-rancher-ingress \
  --cert=tls.crt \
  --key=tls.key

kubectl -n cattle-system create secret generic tls-ca \
  --from-file=cacerts.pem=./cacerts.pem
```

Then deploy Rancher by setting privateCA and ingress_tls  to true
