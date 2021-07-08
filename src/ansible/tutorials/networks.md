## network

Network module allows adding access node to a network, add node and deleting node from a network

## Add node


```yml
---
- name: Add a node to network (create if not exists)
  hosts: localhost
  tasks:
    - name: Add node
      threefold.jsgrid.network_node:
        name: management
        nodes: 
          FED1ZsfbUz3jcJzzqJWyGaoGC61bdN8coKJNte96Fo7k: 10.200.4.0/24
          EECgb24XqKaX5Y6EJJxLczxj9nzCqbq8FKgDwusp9R2A: 10.200.5.0/24
        pool_id: 34
        type: normal


```
Adding nodes to network management on pool 34

## delete node

```yml
---
- name: Delete a node from a network
  hosts: localhost
  tasks:
    - name: Delete a node from a network
      threefold.jsgrid.network_node:
        name: management
        nodes: 
          FED1ZsfbUz3jcJzzqJWyGaoGC61bdN8coKJNte96Fo7k:
          EECgb24XqKaX5Y6EJJxLczxj9nzCqbq8FKgDwusp9R2A:
        state: absent


```

Deleting nodes from network management

## Add access

```yml
---
- name: Add access node to the network
  hosts: localhost
  tasks:
    - name: Add access
      threefold.jsgrid.network_node:
        name: management
        nodes: 
          EECgb24XqKaX5Y6EJJxLczxj9nzCqbq8FKgDwusp9R2A: 10.200.4.0/24
        type: access
      register: result

    - debug:
        msg: "{{ result['wg_config']}}"

```

Adding access node to the network