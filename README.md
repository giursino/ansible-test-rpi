# ansible-test-rpi

## Prerequisites

Install Ansible on the host.

    sudo apt-get install ansible sshpass
    ansible --version

## Prepare target

- install latest raspbian
- add ssh file on boot partition to enable ssh
- setup network interface

## Secrets

I've used ansible vault to storage encrypted variables. The file is
`secrets.yml` and I've created using this command:

    ansible-vault create secrets.yml

using this password: `password`.

To edit this file use this command:

    ansible-vault edit secrets.yml

To decrypt, encrypt,... see `ansible-vault` doc.

To use it: `vars_files: secrets.yml` inside yml main playbook. Then use
the argument `--ask-vault-pass` on `ansible-playbook`.

## Run

    ansible-playbook -vv -i hosts hello.yml

Using vault for encrypted files:

    ansible-playbook -vv --ask-vault-pass -i hosts hello.yml

