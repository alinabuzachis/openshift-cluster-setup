aws.iam
=========

Creates private and public routes, based on AWS tags. Does the following:

    1. Creates a VPC Internet Gateway.
    2. Creates the private routes, using the bastionhost instance ID.
    3. Creates the public route, using the created VPC Internet Gateway.

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
      - role: aws.iam

License
-------

BSD

