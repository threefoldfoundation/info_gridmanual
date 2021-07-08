## farm 

Allows retrieving a farm by id

## complete playbook example


```yml
---
- hosts: localhost
  tasks:
    - name: fetch farm
      farm: 
        farm_id: 1
    
    - name: debug farm
      debug:
        msg: "{{ ansible_facts['farm'] }}"

```