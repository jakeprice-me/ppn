# PPN Raspberry Pi Network Server Configuration

Playbook for `network-01` which is a 2GB Raspberry Pi 4B that provides DNS (using unbound) and DHCP (using dnsmasq) services to my LAN.

## Install Roles & Collections

Install the required Ansible Galaxy Roles & Collections on the local machine.

```sh
ansible-galaxy collection install -r requirements.yml
```

## Variables

### Ansible Vault

Most variables are relatively sensitive and are therefore stored in `vault.yml`.

Create `.vault_password` and pop the password you want to use for the vault in the file. Then create `vault.yml`.

```sh
$ ansible-vault create vault.yml
```

It should contain the following variables.

```yaml
vault_admin_user: 
vault_admin_user_password: 
vault_healthcheck_unison: https://hc-ping.com/<uuid>
vault_interface: eth0
vault_samba_password: 
vault_samba_username: 
vault_static_addr: 
vault_static_dhcp_addr: 
vault_static_dns_addr: 
vault_static_fileserver_addr: 
vault_static_router_addr: 
vault_subnet: 
```

## Run Playbook

```sh
# Run Playbook:
ansible-playbook playbook.yml
```

