aws.jumphost-provision
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

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: localhost
      connection: local
      gather_facts: yes

      roles:
      - role: aws.jumhost-deprovision

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
