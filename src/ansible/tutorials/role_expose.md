## role expose


Exposes a solution on specific IP on domain over the gateway
```yml
---
- hosts: localhost
  vars:
    network_name: management
    gateway_id: 6RZfnjuXVLFdtZh218hn4BLzsoKkTVpweqWECk5YUKud
    identity_name: omar0_test
    pool_id: 419
    trc_secret: "37:super_secret_trc_secret"
    domain_type: managed
    domain: ansible.tfgw-testnet-01.gateway.tf
    solution_port: 7681
    solution_ip: 10.100.0.5
    type: nginx
  roles:
    - threefold.jsgrid.expose

```