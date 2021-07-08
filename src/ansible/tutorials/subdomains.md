## subdomain 

Subdomain module helps creating a subdomain over the gateway

```yml
---
- name: Test js-sdk subdomain module
  hosts: localhost
  tasks:
    - name: "Encrypt metadata"
      threefold.jsgrid.metadata:
        state: encrypt
        metadata:
          test: "test"
        identity_name: asamir_test
      register: encrypted_metadata

    - debug:
        msg: "{{ encrypted_metadata['message']}}"

    - name: "Test create subdomain"
      threefold.jsgrid.subdomain:
        state: present
        pool: 185
        gateway: 9PdutHsdDSxcKUUyDg8ovS1KWh47qLT5R9h5uoFgRUH2
        subdomain: asamir-subdomaintest-asamir.webg1test.grid.tf
        identity_name: asamir_test
        description: "test domain"
        metadata: "{{ encrypted_metadata['message'] }}"
      register: result

    - debug:
        msg: "{{ result }}"

```