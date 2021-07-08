## Role network

ensures a network to exist on pool_id, node_id, with a name network_name

```yml
---
- hosts: localhost
  vars:
    network_name: testnet
    node_id: 8zPYak76CXcoZxRoJBjdU69kVjo7XYU1SFE2NEK4UMqn
    pool_id: 149
  roles:
    - threefold.jsgrid.network

```