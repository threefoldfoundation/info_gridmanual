## container 

Container module helps launching containers on threefold grid using specific flists and configurations like environment variables or starting with coreX for example

## creating a container


```yml
---
- name: Test js-sdk play
  hosts: localhost
  tasks:
    - name: "test container creation"
      threefold.jsgrid.container: 
        pool_id: 3373
        network_name: testans
        flist: "https://hub.grid.tf/omar0.3bot/omarelawady-trc-zinit.flist"
        node_id: Gr8NxBLHe7yjSsnSTgTqGr7BHbyAUVPJqs8fnudEE4Sf
        ip_address: 10.200.0.10
        interactive: true
        description: "test ansible"
        env:
          testkey: testval
      register: result

    - debug:
        msg: "result is: {{ result }}"


```