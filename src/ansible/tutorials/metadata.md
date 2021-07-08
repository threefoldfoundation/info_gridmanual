## metadata

Helps encrypting and decrypting data

```yml
---
- name: Test js-sdk metadata module
  hosts: localhost
  tasks:
    - name: "Test encrypt metadata"
      threefold.jsgrid.metadata:
        state: encrypt
        metadata:
          test: "test"
        identity_name: asamir_test
      register: encrypted_data

    - debug:
        msg: "{{ encrypted_data['message']}}"

    - name: "Test decrypt metadata"
      threefold.jsgrid.metadata:
        state: decrypt
        encrypted_metadata: "{{ encrypted_data['message']}}"
        identity_name: asamir_test 
      register: decrypted_data

    - debug:
        msg: "{{ decrypted_data['message']}}"

```