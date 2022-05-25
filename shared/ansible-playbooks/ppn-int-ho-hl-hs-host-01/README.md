# PPN Virtual Host Server Configuration

Run through the Debian Net Install and create the admin user, also setting an initial password.

## Install Roles & Collections

Install required Ansible Galaxy Roles & Collections.

```sh
ansible-galaxy install -r requirements.yml
```

## Run Playbook

Run `playbook.yml` first, and if successful run `network.yml`.

```sh
ansible-playbook --ask-become-pass playbook.yml
ansible-playbook network.yml
```

Once `playbook.yml` has run once, you will no longer need to run it with `--ask-become-pass`, as private key authentication is now setup.

Be aware that `network.yml` _may_ appear to have stalled when bringing up the bridge interface, but it should generally complete the task without issue, if patient.

