yoshzz.wireguard
================

An Ansible role to install and configure Wireguard.

Each node needs its own private and public key which can be generated with the `wg` tool and need to be added as host 
specific variables in your inventory file:

```yaml
[wireguard]
example.com wg_ip=10.0.1.1 wg_private_key="private_key" wg_public_key="public_key"
```

Requirements
------------

See [meta/main.yml](meta/main.yml)

Role Variables
--------------

See [defaults/main.yml](defaults/main.yml)

Dependencies
------------

See [meta/main.yml](meta/main.yml)

License
-------

MIT

Author Information
------------------

Yosh de Vos <yosh@elzorro.nl>
