## Pools

pools module allows creation, extension of pools on threefold grid

## creation 

```yml
    - name: "test pool creation"
      threefold.jsgrid.pool: 
        farm_name: lochristi_dev_lab
        wallet_name: mainnet
      register: result
```
Here we create a pool on specific farm `lochristi_dev_lab` using wallet `mainnet` using pool module


## extending
```
    - name: "test pool extension"
      threefold.jsgrid.pool: 
        pool_id: "{{ result['message']['reservation_id'] }}"
        wallet_name: mainnet
        sus: 100
        cus: 50
```
here we extend a pool using wallet `mainnet` with resources cus: 50 and sus: 100


## complete playbook


```yml
---
- name: Test js-sdk play
  hosts: localhost
  tasks:
    - name: "test pool creation"
      threefold.jsgrid.pool: 
        farm_name: lochristi_dev_lab
        wallet_name: mainnet
      register: result

    - debug:
        msg: "pool id: {{ result['message']['reservation_id'] }}"

    - name: "test pool extension"
      threefold.jsgrid.pool: 
        pool_id: "{{ result['message']['reservation_id'] }}"
        wallet_name: mainnet
        sus: 100
        cus: 50
```