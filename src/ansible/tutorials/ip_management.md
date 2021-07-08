## ip_management

Helps with getting a free range, getting a free IP address, and getting free public IPs on the farm

```yml
---
- name: Test js-sdk play
  hosts: localhost
  tasks:
    - name: "get free range to update network"
      threefold.jsgrid.ip_management: 
        network_name: k8s
        operation: get_free_range
        fact_name: range_1

    - debug:
        msg: "fact is: {{ ansible_facts['range_1'] }}"

    - name: "get free range to update network"
      threefold.jsgrid.ip_management: 
        network_name: k8s
        operation: get_free_range
        excluded_ranges:
          - "{{ ansible_facts['range_1'] }}"

    - debug:
        msg: "fact is: {{ ansible_facts['ip_range'] }}"

    - name: "get free ip_address to on a node"
      threefold.jsgrid.ip_management: 
        network_name: k8s
        operation: get_ip
        node_id: 8zPYak76CXcoZxRoJBjdU69kVjo7XYU1SFE2NEK4UMqn
        fact_name: address_1
  
    - debug:
        msg: "fact is: {{ ansible_facts['address_1'] }}"

    - name: "get free ip_address to on a node"
      threefold.jsgrid.ip_management: 
        network_name: k8s
        operation: get_ip
        node_id: 8zPYak76CXcoZxRoJBjdU69kVjo7XYU1SFE2NEK4UMqn
        excluded_addresses:
          - "{{ ansible_facts['address_1'] }}"

    - debug:
        msg: "fact is: {{ ansible_facts['ip_address'] }}"

    - name: "get free public ips on a farm"
      threefold.jsgrid.ip_management: 
        operation: get_public_ips
        farm_name: freefarm

    - debug:
        msg: "fact is: {{ ansible_facts['public_ips'] }}"

```