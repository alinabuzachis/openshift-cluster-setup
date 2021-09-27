aws.jumphost-provision
=========

Establishes the AWS settings for a bastion/NAT host. Does the following:

    1. Create VPC
    2. Create Subnets
    3. Create Internet Gateway
    4. Setup Route Tables
    5. Setup Security Groups
    6. Create a Key Pair
    4. Creates the jump host instance.
    5. Add jump host to inventory.

Requirements
------------

Boto and any software required to run Ansible AWS cloud modules.

Role Variables
--------------

See `defaults/main.yml`

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: localhost
      connection: local
      gather_facts: yes

      roles:
      - role: aws.jumhost-provision

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
