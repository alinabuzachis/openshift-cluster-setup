aws.jumphost-deprovision
=========

Deletes the AWS EC2 instance and all the resources initialized by `aws.jumphost-deprovision`.

Requirements
------------

Boto and any software required to run Ansible AWS cloud modules.

Role Variables
--------------

See `defaults/main.yml`

Dependencies
------------

None.

Example Playbook
----------------


    - hosts: localhost
      connection: local
      gather_facts: yes

      roles:
      - role: aws.jumhost-deprovision

License
-------

BSD

