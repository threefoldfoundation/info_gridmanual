## volume

Volume modules helps creating a volume that can be used with a container

```yml
---
- name: Test js-sdk play
  hosts: localhost
  tasks:
    - name: "test volume creation"
      threefold.jsgrid.volume: 
        identity_name: testnet
        pool_id: 149
        node_id: HC1WPUg8GMsbcYakHbHZxeWB1dGhwyvdjGr59dfk7vwE
        size: 1
        type: hdd
      register: result
    
    - debug:
        msg: "result is: {{ result }}"

```