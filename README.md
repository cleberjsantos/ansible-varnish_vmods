varnish_vmods
=============

VMOD checkout from git repository and compile it.

Requirements
------------

* This role requires Ansible 1.2 or higher.


Role Variables
--------------

The variables that can be passed to this role with default values are as follows.

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


Example Playbook
-----------------

Example of usage:

    - hosts: servers
      roles:
        - { role: cleberjsantos.varnish_vmods, tags: [vmod, varnish, cache] }


Custom variables sample:
------------------------

    ---
    
    repos:
      - {vmod: "libvmod-cookie", autogen: True, clone_url: "https://github.com/lkarsten/libvmod-cookie.git", version: "4.1" }
      - {vmod: "libvmod-header", autogen: True, clone_url: "https://github.com/varnish/libvmod-header.git", version: "4.1" }


License
-------

GPLv2

Author Information
------------------

Cleber J Santos
