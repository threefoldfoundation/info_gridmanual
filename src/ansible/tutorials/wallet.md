## wallet
wallet module allows creation, retrieval, deletion and listing of the wallets configured on the system, we will see in the upcoming section examples for each task



## create wallets

```yml
    - name: "Test create Wallet"
      threefold.jsgrid.wallet:
        name: "new_one"
        state: "new"
      ignore_errors: yes
      register: result
    
    - debug:
        msg: "{{ result['out'] }}"
      ignore_errors: yes

```

## import wallet

```yml

    - name: "Test import Wallet"
      threefold.jsgrid.wallet:
        name: "new_one"
        state: "new"
        secret: "SDCDFP73LI527FZPT66LZHDWFRQZB7OVQYB7EZKDLAPVJQGJCKW7CEWM"
      ignore_errors: yes
      register: result
    
    - debug:
        msg: "{{ result['out'] }}"
      ignore_errors: yes

```

## listing wallets

```yml
    - name: "Test list all Wallet"
      threefold.jsgrid.wallet:
        state: "list_all"
      register: result
```

## deleting a wallet

```yml
    - name: "Test delete Wallet"
      threefold.jsgrid.wallet:
        name: "test_mahmoud"
        state: "delete"
      ignore_errors: yes
      register: result
    
```

## Complete playbook

```yml
---
- name: wallet module test
  hosts: localhost
  tasks:
    - name: "Test get Wallet"
      threefold.jsgrid.wallet:
        name: "testmainnet"
        state: "get"
      register: result
    
    - debug:
        msg: "{{ result['out'] }}"
    
    - name: "Test list all Wallet"
      threefold.jsgrid.wallet:
        state: "list_all"
      register: result
    
    - debug:
        msg: "{{ result['out'] }}"

    - name: "Test delete Wallet"
      threefold.jsgrid.wallet:
        name: "test_mahmoud"
        state: "delete"
      ignore_errors: yes
      register: result
    
    - debug:
        msg: "{{ result['message'] }}"
    
    - name: "Test create Wallet"
      threefold.jsgrid.wallet:
        name: "new_one"
        state: "new"
      ignore_errors: yes
      register: result
    
    - debug:
        msg: "{{ result['out'] }}"
      ignore_errors: yes

    - name: "Test import Wallet"
      threefold.jsgrid.wallet:
        name: "new_one"
        state: "new"
        secret: "SDCDFP73LI527FZPT66LZHDWFRQZB7OVQYB7EZKDLAPVJQGJCKW7CEWM"
      ignore_errors: yes
      register: result
    
    - debug:
        msg: "{{ result['out'] }}"
      ignore_errors: yes

```