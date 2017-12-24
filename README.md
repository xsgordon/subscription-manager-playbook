## subscription-manager-playbook-example

## Overview

This playbook:

1. Registers the machine with Red Hat Subscription Manager (RHSM) using the
   credentials provided (refer: Preparation).
2. Uses the RHSM auto-attachment feature to attach subscriptions.
3. Disables all repositories by default, then enables only rhel-7-server-rpms.
4. Updates all available packages, triggering a reboot if necessary for a kernel
   update.

## Preparation

Create a roles/common/vars/rhsm.yaml file, replacing USERNAME with your Red
Hat Subscription Manager usrname and replacing PASSWORD with your Red Hat
Subscription Manager password:

    ---
    - rhsm_username: USERNAME
    - rhsm_password: PASSWORD

Recommended: Encrypt your RHSM information using Ansible vault:

    $ ansible-vault encrypt roles/common/vars/rhsm.yaml

## Execution

$ ansible-playbook subscription-manager-playbook.yaml --ask-vault-pass
