## Proxy


Proxy module exposes solutions on the gateways using TRC (tcprouter client)
```yml
---
- name: Test js-sdk tcp reverse proxy module
  hosts: localhost
  tasks:
    - name: "Encrypt metadata"
      threefold.jsgrid.metadata:
        state: encrypt
        metadata:
          test: "test"
        identity_name: asamir_test
      register: encrypted_metadata

    - name: "Test create proxy"
      threefold.jsgrid.proxy:
        state: present
        pool: 185
        gateway: 9PdutHsdDSxcKUUyDg8ovS1KWh47qLT5R9h5uoFgRUH2
        domain: asamir-subdomaintest-asamir.webg1test.grid.tf
        trc_secret: "104:12345678"
        identity_name: asamir_test
        description: "test domain"
        metadata: "{{ encrypted_metadata['message'] }}"
      register: result

    - debug:
        msg: "{{ result }}"

```