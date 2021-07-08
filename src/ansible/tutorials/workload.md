## workload 
the workload module helps with getting a specific workload facts, list workloads, filtering against specific type of workloads and deletion of workloads


```yml
---
- name: Test js-sdk play
  hosts: localhost
  tasks:
    - name: "test single workload facts"
      threefold.jsgrid.workload: 
        wid: 1185
      register: result

    - debug:
        msg: "result: {{ result }}"

    - name: "test list workload facts"
      threefold.jsgrid.workload: 
      register: result

    - debug:
        msg: "result: {{ result }}"

    - name: "testfilter"
      threefold.jsgrid.workload: 
        types:
          - network_resource
        match:
          info.node_id: 8zPYak76CXcoZxRoJBjdU69kVjo7XYU1SFE2NEK4UMqn
          name: testneterhoeh
      register: result

    - debug:
        msg: "result: {{ result }}"

    - name: "test delete deployed workload"
      threefold.jsgrid.workload: 
        wid: 1174
        state: deleted
      register: result

    - debug:
        msg: "result: {{ result }}"

    - name: "test redeploy deleted workload"
      threefold.jsgrid.workload: 
        wid: 1174
        state: present
      register: result

    - debug:
        msg: "result: {{ result }}"


```