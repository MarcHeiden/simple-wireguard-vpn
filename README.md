# simple-wireguard-vpn

Ansible Playbook to set up a simple wireguard vpn on an ubuntu server.

_Inspired by [ansible-easy-vpn](https://github.com/notthebee/ansible-easy-vpn)_

## What does the playbook do?

- Setup ssh key authentification and hardening ssh
- Install basic ufw rules
- Configure wireguard and generate client config files and qrcodes which can be found under `~/wireguard` on your local machine

## Usage

```shell
> ansible-playbook run.yml
```

## Prerequisites

### Install ansible

```shell
> sudo apt-get install ansible
```

### Install required ansible collections

```shell
> ansible-galaxy install -r requirements.yml
```

## Customization

- Add your servers to the inventory
- Edit the variables in `group_vars/vars.yml`
- Create a `vault.yml` file inside `group_vars` and provide your credentials:

  ```yaml
  # file: group_vars/vault.yml
  ---
  vault_new_ansible_user_password: ""
  vault_user_password: ""
  vault_ssh_key_passphrase_: ""
  vault_localhost_password: ""
  vault_ssh_password1: ""
  vault_ssh_password2: ""
  ```

  and encrypt the file with:

  ```shell
  > ansible-vault encrypt group_vars/vault.yml
  ```
