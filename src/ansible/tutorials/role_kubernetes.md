## Role kubernetes

Allows higherlevel abstraction to provision kubernetes


```yml
---
- hosts: localhost
  vars:
    network_name: testnet
    pool_id: 149
    cluster_secret: passwd12#$
    ssh_keys:
      - "/home/maged/Keys/id_rsa.pub"
    size: 15
    cru: 1
    mru: 2
    sru: 25
  roles:
    - threefold.jsgrid.kubernetes

```