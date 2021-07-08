## zdb

ZDB module allows provisioning zdb containers on the grid, allows configuring the size, the mode, password and the disk type too

```yml
---
- name: Test js-sdk ZDB module
  hosts: localhost
  tasks:
    - name: "Test create ZDB"
      threefold.jsgrid.zdb:
        state: present
        pool: 229 
        node: 26ZATmd3K1fjeQKQsi8Dr7bm9iSRa3ePsV8ubMcbZEuY
        size: 2
        mode: "SEQ"
        password: ""
        disk_type: "SSD"
        identity_name: asamir_test
      register: result

    - debug:
        msg: "{{ result }}"
```