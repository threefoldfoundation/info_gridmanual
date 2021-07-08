## Role container

Allows higherlevel abstraction around containers


```yml
---
- hosts: localhost
  vars:
    - pool_id: 229
    - network_name: newnet
    - cpu: 1
    - memory: 1024 # MBs
    - disk_size: 10 # GBs
    - metadata:
      test: "test"
  roles:
    - threefold.jsgrid.container

```