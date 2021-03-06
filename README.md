[![Build status](https://travis-ci.org/acoston/Ansible-EfficientIP.svg)](https://travis-ci.org/acoston/Ansible-EfficientIP)

# EfficientIP Ansible module
An EfficientIP Solidserver module for Ansible

## Disclaimer

This module is still in development.

## Install

- put it in your Ansible module directory
- you also need to install the "requests" py module

### Examples
```
tasks:
- name: list space
  efficientip:
    eip_server: server.mydomain.com
    eip_username: dummyusername
    eip_password: dummypassword
    space: LIST

- name: list usable subnet from a space
  efficientip:
    eip_server: server.mydomain.com
    eip_username: dummyusername
    eip_password: dummypassword
    subnet: LIST
    space: NY_space
    classparam: 'metadata1=somedata'
    -or-
    classname: myclass

- name: find one free IP address on a subnet
  efficientip:
    eip_server: server.mydomain.com
    eip_username: dummyusername
    eip_password: dummypassword
    hostaddr: FIND_FREE
    subnet_id=4

- name: add IP on space
  efficientip:
    eip_server: server.mydomain.com
    eip_username: dummyusername
    eip_password: dummypassword
    type: A
    state: present
    space: NY_space
    record: test.mydomain.com
    hostaddr: 127.0.0.1

- name: delete IP on space
  efficientip:
    eip_server: server.mydomain.com
    eip_username: dummyusername
    eip_password: dummypassword
    type: A
    state: absent
    space: NY_space
    hostaddr: 127.0.0.1

- name: add CNAME
  efficientip:
    eip_server: serer.mydomain.com
    eip_username: dummyusername
    eip_password: dummypassword
    type: CNAME
    alias_fqdn: alias.mydomain.net
    alias_value: hostname.mydomain.net
    alias_ttl: 600

```
