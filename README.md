# Local Travis simulator

  A lightweight and focused Ansible tester powered by Vagrant.

  Designed for provisioning ansible roles before being destroyed for the purposes of testing roles in the same fashion as travis for private repositories.

## Usage

### Configuration

#### Instructions

  Place a valid `variables.yml`, `requirements.yml` and `playbook.yml` inside the provisioning folder and you can get started!

  Private roles can be placed in the provisioning directory for testing if your playbook refers to those roles.

#### Examples

##### Example provisioning/variables.yml

    ---
    myvar: 'my variable'

##### Example provisioning/requirements.yml

    ---
    - name: geerlingguy.php

##### Example provisioning/playbook.yml

    ---
    - hosts: all
      roles:
      - role: geerlingguy.php


### Starting

    vagrant up --provision

### Restarting

    vagrant halt; vagrant destroy

## Credits

  I've been looking for something minimalist to run Ansible roles in a travis-style.

  Original fork from Brad Westfall

  [Brad Westfall's video](https://www.youtube.com/watch?v=crvJ2C7Hr_g)