# Provision a Red Hat OpenShift Cluster on AWS
This repository contains a set of playbooks and roles which provisions and deprovisions an Amazon EC2 instance acting as a jump server and a Red Hat OpenShift Cluster on AWS. The Amazon EC2 jump server serves as management server from where we ran the OpenShift installer and CLI tasks.

The playbooks build all the required components (including VPC, networking, security groups, etc.), and you can modify the `vars/main.yml` file to use different defaults if you'd like.

## Pre-requisite

### AWS
You need an AWS Account and Admin User credentials. Create a vault file with AWS credentials:
  1. Go to root of this project and execute this command: ansible-vault create aws_keys.yml
  2. Choose a password
  3. Update the newly created file with the following information:
```
aws_access_key: AKxxxxxxxxxxxxx
aws_secret_key: xxxxxxxxxxxxxxx 
```
*You can find your aws credentials in the security credentials tab on AWS console.

### Red Hat OpenShift Container Platform
You need a Valid Red Hat Subscription. To pull secrets to be used by OpenShift Container Platform (OCP) 4.x (used by [roles/ocp.cluster-setup/templates/install-config.yaml.j2](https://github.com/alinabuzachis/openshift-cluster-setuptemplates/install-config.yaml.j2) you need to your offline access token found at https://cloud.redhat.com/openshift/token (login required), and according to the documentation found in the OCP [install guide](https://cloud.redhat.com/openshift/install).

You can create a vault file with the token:
  1. Go to root of this project and execute this command: `ansible-vault create ocp_token.yml`
  2. Choose a password
  3. Update the newly created file with the following information:
```
ocp_pull_secrets_offline_token: eyK######################
```

## Usage
Make sure you have boto3 and botocore installed locally: `pip3 install boto3 botocore`.

Install requirements:
```
$ ansible-galaxy install -r requirements.yml
```
Deploy the Amazon EC2 jump server:

```
$ ansible-playbook deploy.yml
```
Once the Amazon EC2 jump server has been set up,
Get pull secrets to be used by OpenShift Container Platform (OCP) 4.x to pull images from registries that require authentication.
Provision a Red Hat OpenShift Cluster on AWS in the environment:

```
$ ansible-playbook openshift_install.yml --ask-vault-password
```
Then, you can ssh into the Amazon EC2 jump server using `ssh -i ~/.ssh/key_bench.pub ubuntu@x.x.x.x` and to access the cluster as the `system:admin` user when using oc, run `export KUBECONFIG=~/ocp/auth/kubeconfig`.

## Cleanup
Once you don't need anymore the setup, run the destroy.yml playbook to destroy the test environment:
```
$ ansible-playbook destroy.yml
```
