Commands to run:

## Setup venv

```
$: virtualenv venv
...
$: source venv/bin/activate
...
$: pip freeze
appdirs==1.4.3
packaging==16.8
pyparsing==2.2.0
six==1.10.0
```

## Install ansible

$: pip install -U ansible
...
$: pip freeze
ansible==2.2.1.0
appdirs==1.4.3
asn1crypto==0.22.0
cffi==1.10.0
cryptography==1.8.1
enum34==1.1.6
idna==2.5
ipaddress==1.0.18
Jinja2==2.8.1
MarkupSafe==1.0
packaging==16.8
paramiko==2.1.2
pyasn1==0.2.3
pycparser==2.17
pycrypto==2.6.1
pyparsing==2.2.0
PyYAML==3.12
six==1.10.0
$: ansible --version
ansible 2.2.1.0
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/usr/share/ansible']
```

## Setup your host to be configured


```
# ssh to host to accept host key
# ssh to host install python
```

## Change directory to inventory/1, modify inventory file as appropriate

```
$: ansible myhosts -i inventory --list-hosts
  hosts (1):
    199.19.215.26

$: ansible all -i inventory1 -m ping
199.19.215.26 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}

$: ansible myhosts -i inventory -m ping
199.19.215.26 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
$: ansible myhosts -i inventory -m setup
...
```

# Ansible-playbook

## Change directory to examples/3


```
$: cat playbook.yml 

- hosts: all
  become: true
  tasks:
  - debug: msg="debug {{inventory_hostname}}"


$: ansible-playbook -i inventory playbook.yml

PLAY [all] *********************************************************************

TASK [setup] *******************************************************************
ok: [199.19.215.26]

TASK [debug] *******************************************************************
ok: [199.19.215.26] => {
    "msg": "debug 199.19.215.26"
}

PLAY RECAP *********************************************************************
199.19.215.26              : ok=2    changed=0    unreachable=0    failed=0   
```

## For examples 3-8 you'll run exactly as above


# References

* http://docs.ansible.com/ansible/debug_module.html
* http://docs.ansible.com/ansible/playbooks_intro.html





