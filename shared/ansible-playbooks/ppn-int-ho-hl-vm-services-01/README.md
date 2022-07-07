# PPN Virtual Server Configuration

## services-01

This playbook will setup the virtual server that runs general services and web applications on PPN.

## Install Roles & Collections

Install required Ansible Galaxy Roles & Collections.

```sh
ansible-galaxy install -r requirements.yml
```

## Ansible Vault

The following secrets are kept in `vault.yml`.

```yml
vault_admin_user: <value>
vault_bible_build_healthcheck: https://hc-ping.com/<uuid>
vault_log_build_healthcheck: https://hc-ping.com/<uuid>
vault_unison_healthcheck: https://hc-ping.com/<uuid>
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
