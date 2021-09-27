ocp.cluster-setup
=========

Proivion a Red Hat OpenShift Cluster on AWS. It does the following:

    1. Downloads OpenShift on AWS installer
    2. Create an OpenShift cluster using the information provided inside templates/install-comfig.yml.j2
    3. Download OpenShift Command-line tool.

Requirements
------------

Boto and any software required to run Ansible AWS cloud modules. 

An offline access token found at https://cloud.redhat.com/openshift/token (login required), and according to the documentation found in the OCP [install guide](https://cloud.redhat.com/openshift/install).

Role Variables
--------------

* `ocp_route53_hosted_zone`
    * Amazon Route53 hosted zone.
* `ocp_cluster_name`
    * OpenShift cluster name.
* `ocp_cluster_aws_region`
    * AWS region used to deploy the OpenShift cluster.
*  `ocp_pull_secrets`
    * Acquired from `oasis_roles.ocp_pull_secrets`.

Dependencies
------------

* `oasis_roles.ocp_pull_secrets`

Example Playbook
----------------

    - hosts: localhost
      connection: local
      gather_facts: yes
      
      roles:
      - role: ocp_pull_secrets
      - role: ocp.cluster-setup

License
-------

BSD
