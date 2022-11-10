# PPN Virtual Host Server Configuration

## host-01

This playbook will setup the host server that runs virtual machines on PPN.

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

## Run Playbook

Run the playbook as shown below.

```sh
ansible-playbook playbook.yml
```

