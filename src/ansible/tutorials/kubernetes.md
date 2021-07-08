## Kubernetes

Helps provisioning kubernetes clusters on the Grid

## creating master
```yml
    - name: "test k8s master creation"
      threefold.jsgrid.kubernetes: 
        identity_name: testnet
        pool_id: 149
        node_id: 26ZATmd3K1fjeQKQsi8Dr7bm9iSRa3ePsV8ubMcbZEuY
        network_name: k8s
        cluster_secret: password12#$
        ip_address: "10.200.0.212"
        size: 15
        ssh_keys: "~/Keys/id_rsa.pub"
        description: "k8s master from ansible"
      register: result
```

## creating worker

```yml
    - name: "test k8s worker creation"
      threefold.jsgrid.kubernetes: 
        identity_name: testnet
        pool_id: 149
        node_id: 8zPYak76CXcoZxRoJBjdU69kVjo7XYU1SFE2NEK4UMqn
        network_name: k8s
        cluster_secret: password12#$
        ip_address: "10.200.1.235"
        size: 15
        master_ip: "10.200.0.212"
        ssh_keys: "~/Keys/id_rsa.pub"
        description: "k8s worker from ansible"
      register: result
```

## complete playbook


```yml
---
- name: Test js-sdk play
  hosts: localhost
  tasks:
    - name: "test k8s master creation"
      threefold.jsgrid.kubernetes: 
        identity_name: testnet
        pool_id: 149
        node_id: 26ZATmd3K1fjeQKQsi8Dr7bm9iSRa3ePsV8ubMcbZEuY
        network_name: k8s
        cluster_secret: password12#$
        ip_address: "10.200.0.212"
        size: 15
        ssh_keys: "~/Keys/id_rsa.pub"
        description: "k8s master from ansible"
      register: result
    
    - debug:
        msg: "result is: {{ result }}"

    - name: "test k8s worker creation"
      threefold.jsgrid.kubernetes: 
        identity_name: testnet
        pool_id: 149
        node_id: 8zPYak76CXcoZxRoJBjdU69kVjo7XYU1SFE2NEK4UMqn
        network_name: k8s
        cluster_secret: password12#$
        ip_address: "10.200.1.235"
        size: 15
        master_ip: "10.200.0.212"
        ssh_keys: "~/Keys/id_rsa.pub"
        description: "k8s worker from ansible"
      register: result
    
    - debug:
        msg: "result is: {{ result }}"

```