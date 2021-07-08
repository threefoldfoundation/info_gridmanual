## Concepts

Here we define some basic ansible concepts that we will use in the rest of the documentation (aligned with ansible upstream)

TODO: link to upstream and small description
## ansible
Ansible is an IT automation tool. It can configure systems, deploy software, and orchestrate more advanced IT tasks such as continuous deployments or zero downtime rolling updates.

Ansible’s main goals are simplicity and ease-of-use. It also has a strong focus on security and reliability, featuring a minimum of moving parts, usage of OpenSSH for transport (with other transports and pull modes as alternatives), and a language that is designed around auditability by humans–even those not familiar with the program.



## ansible-playbook
Playbooks are the language by which Ansible orchestrates, configures, administers, or deploys systems. They are called playbooks partially because it’s a sports analogy, and it’s supposed to be fun using them. They aren’t workbooks :)



## ansible-inventory
A file (by default, Ansible uses a simple INI format) that describes Hosts and Groups in Ansible. Inventory can also be provided via an Inventory Script (sometimes called an “External Inventory Script”).

## ansible-vault
Ansible Vault encrypts variables and files so you can protect sensitive content such as passwords or keys rather than leaving it visible as plaintext in playbooks or roles. To use Ansible Vault you need one or more passwords to encrypt and decrypt content. If you store your vault passwords in a third-party tool such as a secret manager, you need a script to access them. Use the passwords with the ansible-vault command-line tool to create and view encrypted variables, create encrypted files, encrypt existing files, or edit, re-key, or decrypt files. You can then place encrypted content under source control and share it more safely.

## ansible-galaxy

An online resource for finding and sharing Ansible community content. Also, the command-line utility that lets users install individual Ansible Collections, for example`` ansible-galaxy install community.crypto``.


## collection:
 A packaging format for bundling and distributing Ansible content, including plugins, roles, modules, and more. Collections release independent of other collections or ansible-base so features can be available sooner to users. Some collections are packaged with Ansible (version 2.10 or later). You can install other collections (or other versions of collections) with ansible-galaxy collection install <namespace.collection>.
## roles
Roles are units of organization in Ansible. Assigning a role to a group of hosts (or a set of groups, or host patterns, and so on) implies that they should implement a specific behavior. A role may include applying certain variable values, certain tasks, and certain handlers – or just one or more of these things. Because of the file structure associated with a role, roles become redistributable units that allow you to share behavior among playbooks – or even with other users.

## modules
Modules are the units of work that Ansible ships out to remote machines. Modules are kicked off by either /usr/bin/ansible or /usr/bin/ansible-playbook (where multiple tasks use lots of different modules in conjunction). Modules can be implemented in any language, including Perl, Bash, or Ruby – but can leverage some useful communal library code if written in Python. Modules just have to return JSON. Once modules are executed on remote machines, they are removed, so no long running daemons are used. Ansible refers to the collection of available modules as a library.
## facts

Facts are simply things that are discovered about remote nodes. While they can be used in playbooks and templates just like variables, facts are things that are inferred, rather than set. Facts are automatically discovered by Ansible when running plays by executing the internal setup module on the remote nodes. You never have to call the setup module explicitly, it just runs, but it can be disabled to save time if it is not needed or you can tell ansible to collect only a subset of the full facts via the gather_subset: option. For the convenience of users who are switching from other configuration management systems, the fact module will also pull in facts from the ohai and facter tools if they are installed. These are fact libraries from Chef and Puppet, respectively. (These may also be disabled via gather_subset:)


For more information on ansible concepts please check the [glossary](https://docs.ansible.com/ansible/latest/reference_appendices/glossary.html)