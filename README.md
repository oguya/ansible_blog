## Mjanja webserver

Playbooks for base and initial configuration of Mjanja web server.

### To use
Create a new Ubuntu 14.04 host, add a user account, copy your SSH public key, then execute:

    ansible-playbook site.yml -i hosts -K
