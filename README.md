varnish_vmods
=============

[![Ansible Role](https://img.shields.io/ansible/role/5964.svg)](https://galaxy.ansible.com/list#/roles/5964)
[![Travis CI](https://img.shields.io/travis/cleberjsantos/ansible-varnish_vmods/master.svg)](http://travis-ci.org/cleberjsantos/ansible-varnish_vmods)
[![Tag](https://img.shields.io/github/tag/cleberjsantos/ansible-varnish_vmods.svg)]()

VMOD checkout from git repository and compile it.

Requirements
------------

* This role requires Ansible 1.2 or higher.


Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml).

    # The version to checkout
    version: HEAD

    # Array of dicts to clone
    repos: []

    # Destination path to clone
    temp_clone: /tmp

    # Varnish VMODs destination path installation
    VMODDIR: /usr/lib/varnish/vmods

    # Varnish source directory (Used with Varnish 3.x)
    VARNISHSRC: 

    # Do you want to build this repo? 
    build: true

    # The build configuration command
    configure_cmd: "./configure"

    # The make build command
    make_cmd: make

    # The installation command
    makeinstall_cmd: make install


Repository variables for checkout and run
------------------------------------------
   
    # VMOD name
    vmod: "libvmod-header"

    # If there's autogen.sh script and then want to run
    autogen: True # False if there's no autogen.sh script

    # Where to clone from?
    clone_url: "https://github.com/varnish/libvmod-header.git"


Example Playbook
-----------------

Example of usage:

    - hosts: servers
      roles:
        - { role: cleberjsantos.varnish_vmods, vmod: "libvmod-cookie", autogen: True, clone_url: "https://github.com/lkarsten/libvmod-cookie.git", version: "4.1", tags: [vmod, varnish] }


Custom variables sample:
------------------------

Eg. you can add custom variables in the group_vars or host_vars. 

    ---
    # file: /etc/ansible/group_vars/all
    
    repos:
      - {vmod: "libvmod-cookie", autogen: True, clone_url: "https://github.com/lkarsten/libvmod-cookie.git", version: "4.1" }
      - {vmod: "libvmod-header", autogen: True, clone_url: "https://github.com/varnish/libvmod-header.git", version: "4.1" }


License
-------

GPLv2

Author Information
------------------

Cleber J Santos
