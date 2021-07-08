## requirements

### js-grid
- git clone https://github.com/threefoldtech/js-grid/
- poetry install
- poetry shell

### ansible
within the virtual environment of js-grid we should add ansible dependencies e.g (ansible-playbook, ansible-galaxy, ansible-vault, .. etc) by install the ansible package

- pip3 install ansible

## Adding ansible galaxy

- To build a package collection to be used with the threefold grid execute: `ansible-galaxy collection build`
- And to install that package, execute: `ansible-galaxy collection install threefold-jsgrid-0.1.0.tar.gz`


TODO: easier way to add the collection and the dependencies without bothering with virtualenv?