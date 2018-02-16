yoshz.wireguard
================

An Ansible role to install and configure Wireguard.


Requirements
------------

See [meta/main.yml](meta/main.yml)

Role Variables
--------------

See [defaults/main.yml](defaults/main.yml)

Dependencies
------------

See [meta/main.yml](meta/main.yml)

Usage
-----

Each node needs its own private and public key which can be generated with the `wg` tool.

Create a playbook `wireguard.yml` with this role:

```yaml
- hosts: wireguard
  roles:
  - yoshz.wireguard

```
 
Install Wireguard without configuring it:

```bash
ansible-playbook -i <inventory> wireguard.yml --tags install
```
 
Generate a private key for each host:

```bash
ansible -i <inventory> wireguard -m shell -a 'export KEY=$(wg genkey); echo "Private key: $KEY"; echo -n "Public key: "; echo $KEY | wg pubkey'
```

Update your inventory file and update the private key for each host

```yaml
[wireguard]
node1 wg_ip=10.0.1.1 wg_private_key="private_key" wg_public_key="public_key"
node2 wg_ip=10.0.1.2 wg_private_key="private_key" wg_public_key="public_key"
```

Configure Wireguard:

```bash
ansible-playbook -i <inventory> wireguard.yml --tags configure
```

License
-------

MIT

Author Information
------------------

Yosh de Vos <yosh@elzorro.nl>
