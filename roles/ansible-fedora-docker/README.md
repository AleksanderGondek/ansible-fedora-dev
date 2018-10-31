ansible-fedora-docker
=========

Ansible role to install and configure docker on Fedora. 
Optionally it may also install docker-compose. 

This role was created for training purposes, as they are many similar ones.

Requirements
------------

Internet connectivity (proxy is not yet supported)

Role Variables
--------------

* name: *{type}* - description


Example Playbook
----------------

    - name: Install docker ce
      import_role:
        name: ansible-fedora-docker
      vars:
        ansible_fedora_docker_version: '1.1.1'

License
-------

MIT License
