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

* ansible_fedora_docker_purge: *{boolean}* indicates if docker data dir should be purged, defaults to true
* ansible_fedora_docker_yum_repos: *{list of dicts}* yum repositories the docker can be installed from
* ansible_fedora_docker_data_root: *{string}* directory that docker should use as data dir
* ansible_fedora_docker_log_driver: *{string}*  docker log driver to use
* ansible_fedora_docker_log_opts: *{dict}* key-values which should correspond to configurable options of log driver
* ansible_fedora_docker_storage_driver: *{string}* docker storage driver to use
* ansible_fedora_docker_compose_install: *{boolean}* indicates if docker-compose should be installed
* ansible_fedora_docker_compose_version: *{string}* indicates which version of docker-compose should be installed
* ansible_fedora_docker_compose_checksum: *{string}* checksum of downloaded binary
* ansible_fedora_docker_compose_install_path: *{string}* indicates where docker-compose should be installed
* ansible_fedora_docker_cron_jobs: *{list of dicts}* cron jobs that should be setup (i.e. docker system prune)
  ```
    - name: "Docker system prune - once a day"
      file_name: "docker_system_prune"
      job: 'docker system prune -af &> /dev/null'
      schedule: ["0", "0", "*", "*", "*"]
      user: "{{ (ansible_fedora_docker_users | first) | default('root') }}"
  ```


Example Playbook
----------------

    - name: Install docker ce
      import_role:
        name: ansible-fedora-docker
      vars:

License
-------

MIT License
