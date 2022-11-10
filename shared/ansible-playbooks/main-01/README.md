# PPN Main Server Configuration

## main-01

This playbook will setup the server that runs the vast majority of self-hosted services on my LAN.

## Install Roles & Collections

Install required Ansible Galaxy Roles & Collections.

```sh
ansible-galaxy install -r requirements.yml
```

## Ansible Vault

The following secrets are kept in `vault.yml`.

```yml
vault_admin_user: <username>
vault_borg_my_passphrase: <passphrase>
vault_borg_my_remote_passphrase: <passphrase>
vault_dns_ip: <ip>
vault_gateway_ip: <ip>
vault_host_01_ip: <ip>
vault_meilisearch_api_key: <key>
vault_samba_user_1_password: <password>
vault_samba_user_1_username: <username>
vault_samba_user_2_password: <password>
vault_samba_user_2_username: <username>
```

The `vault.yml` file is encrypted and password protected. `.vault_password` which stores the password to open `vault.yml` is not committed to version control. If `vault.yml` is ever "lost", simply create a new `.vault_password` file containing a random passphrase and a new `vault.yml` file and provide values for the above vault variables (`ansible.cfg` specifies that `ansible-vault` should use the password in `.vault_password` for creating and editing `vault.yml`). 

Example below.

```sh
echo <password> > .vault_password
ansible-vault create vault.yml
```

## Issues

If you have issues with Loki getting enabled, run the below on the server manually.

```sh
docker plugin install  grafana/loki-docker-driver:latest --alias loki --grant-all-permissions
```

## Run Playbook

Run the playbook as shown below.

```sh
# Initial run:
ansible-playbook playbook.yml --ask-become-pass

# Every other run:
ansible-playbook playbook.yml
```

