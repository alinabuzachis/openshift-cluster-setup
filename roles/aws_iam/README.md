aws_iam
=========

Creates IAM roles and policies.

Requirements
------------

Boto and any software required to run Ansible AWS cloud modules.

Role Variables
--------------

See `defaults/main.yml`.

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: localhost
      connection: local
      gather_facts: yes

      roles:
      - role: aws_iam

License
-------

BSD

