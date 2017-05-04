ansible-role-asterixdb
======================

[![Build Status](https://travis-ci.org/kevincoakley/ansible-role-asterixdb.svg?branch=master)](https://travis-ci.org/kevincoakley/ansible-role-asterixdb)

Install AsterixDB (single machine and clustered) - https://asterixdb.apache.org/ . Tested with CentOS 7 and Ubuntu 16.04

Requirements
------------

None

Role Variables
--------------

See defaults/main.yml and the example inventory below

Dependencies
------------

None

Example Playbook
----------------

    - name: AsterixDB Single Machine
      hosts: asterixdb-single
      become: yes
      become_method: sudo
        
      roles:
      - ansible-role-asterixdb
            
    - name: AsterixDB Clustered
      hosts: asterixdb-clustered
      become: yes
      become_method: sudo
    
      vars:
        - asterixdb_cluster: True
        - asterixdb_ansible_host_group: asterixdb-clustered
    
      roles:
        - ansible-role-asterixdb

Example Inventory
-----------------

    [asterixdb-single]
    asterixdb-single ansible_host=127.0.0.1
    
    [asterixdb-clustered]
    asterixdb-cluster-0 ansible_host=127.0.0.1 asterixdb_master=True 
    asterixdb-cluster-1 ansible_host=127.0.0.1 asterixdb_master=False 
    asterixdb-cluster-2 ansible_host=127.0.0.1 asterixdb_master=False 

License
-------

BSD

Author Information
------------------

Kevin Coakley (https://github.com/kevincoakley)
