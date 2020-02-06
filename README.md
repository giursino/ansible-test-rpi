# ansible-test-rpi

## Prerequisites

Install Ansible on the host.

    sudo apt-get install ansible sshpass
    ansible --version

## Prepare target

- install latest raspbian
- add ssh file on boot partition to enable ssh
- setup network interface

## Run

    ansible-playbook -vv -i hosts hello.yml

