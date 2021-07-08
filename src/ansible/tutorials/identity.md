Here we will be discussing how to define a playbook to get, create, list and delete identities on tfgrid



## Task 1 (get an identity/create)


```yml
    - name: "Test get identity"
      threefold.jsgrid.identity:
        instance_name: ansident
        state: present
        tname: ansident.3bot
        email: ansident@incubaid.com
        words: nuclear file soda sting load frame field hold virus metal tragic grain owner skirt journey onion spirit until immune theory lunar fever scrub pelica
        explorer: devnet
      register: identity
    
    - debug: var=identity
```
Here we define a task to get an identity, we create an identity using the identity module, giving an instance name, and the required fields to create a new identity on the grid (3botname, email, and words and explorer network) and we ask to register it


## Task 2 (setting default identity)

```yml
    - name: "Test set default identity"
      threefold.jsgrid.identity:
        instance_name: ansident
        state: present
        set_default: yes

```
the identity module allows using `set_default` on identity  (now this identity will be the default across the sdk)

## Task (listing identities)

```yml
    - name: "Test list identities"
      threefold.jsgrid.identity:
        state: list
      register: result

    - debug:
        msg: "{{ result['message']}}"
```



## Task (delete identity)

```yml
    - name: "Test delete identity"
      threefold.jsgrid.identity:
        instance_name: ansident
        state: absent
```
here we ask ansible to ensure the state of the identity `ansident` to be absent (which will invoke removal from the system)



## Complete playbook

```yml
---
- name: Test js-sdk identity module
  hosts: localhost
  tasks:
    - name: "Test get identity"
      threefold.jsgrid.identity:
        instance_name: ansident
        state: present
        tname: ansident.3bot
        email: ansident@incubaid.com
        words: nuclear file soda sting load frame field hold virus metal tragic grain owner skirt journey onion spirit until immune theory lunar fever scrub pelica
        explorer: devnet
      register: identity
    
    - debug: var=identity
    
    - name: "Test set default identity"
      threefold.jsgrid.identity:
        instance_name: ansident
        state: present
        set_default: yes

    - name: "Test list identities"
      threefold.jsgrid.identity:
        state: list
      register: result

    - debug:
        msg: "{{ result['message']}}"

    - name: "Test delete identity"
      threefold.jsgrid.identity:
        instance_name: ansident
        state: absent
    
    - name: "Test list identities"
      threefold.jsgrid.identity:
        instance_name: ansident
        state: list
      register: result

    - debug:
        msg: "{{ result['message']}}"

```