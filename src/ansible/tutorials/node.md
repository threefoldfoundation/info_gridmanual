## node module

Helps getting node information (capacity node or gateway node)

```yml
---
- name: Test js-sdk play
  hosts: localhost
  tasks:
    - name: "get node info"
      threefold.jsgrid.node: 
        node_id: "BHx2mKZ3MkqG4pmXPVwe45ivZycazMbCrenV6NDZHUpt"
      register: result

    - debug:
        msg: "fact is: {{ ansible_facts['BHx2mKZ3MkqG4pmXPVwe45ivZycazMbCrenV6NDZHUpt'] }}"

    - name: "get gateway data"
      threefold.jsgrid.node: 
        node_id: "EwPS7nPZHd5KH6YH7PtbmUpJUyWgseqsqS7cGhjXLUjz"
        gateway: true
      register: result

    - debug:
        msg: "fact is: {{ ansible_facts['EwPS7nPZHd5KH6YH7PtbmUpJUyWgseqsqS7cGhjXLUjz'] }}"
```