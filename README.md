ansible-module-lxd
==================

Ansible module to install and configure LXD on your system and create,modify,delete LXD containers.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

```
lxd_ubuntu_packages:
    - lxd
    - python-pip
    - python-lxc
```

```
lxd_bridgeconf_ipv4_addr: "10.254.254.1"
lxd_bridgeconf_ipv4_netmask: "255.255.255.0"
lxd_bridgeconf_ipv4_network: "10.254.254.1/24"
lxd_bridgeconf_ipv4_dhcp_range: "10.254.254.2,10.254.254.253"
lxd_bridgeconf_ipv4_dhcp_max: 252
lxd_bridgeconf_ipv4_nat: true
lxd_bridgeconf_ipv6_nat: false
lxd_bridgeconf_ipv6_proxy: false

lxd_preloadimages:
    - { i: 'images:/ubuntu/precise/amd64', alias: 'ubuntu-12.04' }
    - { i: 'images:/ubuntu/trusty/amd64',  alias: 'ubuntu-14.04' }
    - { i: 'images:/ubuntu/xenial/amd64',  alias: 'ubuntu-16.04' }
    - { i: 'images:/centos/6/amd64',       alias: 'centos-6' }
    - { i: 'images:/centos/7/amd64',       alias: 'centos-7' }
    - { i: 'images:/debian/wheezy/amd64',  alias: 'debian-7' }
    - { i: 'images:/debian/jessie/amd64',  alias: 'debian-8' }
    - { i: 'images:/alpine/3.0/amd64',     alias: 'alpine-3.0' }
    - { i: 'images:/alpine/3.1/amd64',     alias: 'alpine-3.1' }
    - { i: 'images:/alpine/3.2/amd64',     alias: 'alpine-3.2' }
    - { i: 'images:/alpine/3.3/amd64',     alias: 'alpine-3.3' }
    - { i: 'images:/alpine/3.4/amd64',     alias: 'alpine-3.4' }
    - { i: 'images:/alpine/edge/amd64',    alias: 'alpine-edge' }
    - { i: 'images:/fedora/22/amd64',      alias: 'fedora-22' }
    - { i: 'images:/fedora/23/amd64',      alias: 'fedora-23' }
    - { i: 'images:/fedora/24/amd64',      alias: 'fedora-24' }
    - { i: 'images:/gentoo/current/amd64', alias: 'gentoo-current' }
    - { i: 'images:/opensuse/13.2/amd64',  alias: 'opensuse-13.2' }
    - { i: 'images:/oracle/6/amd64',       alias: 'oracle-6' }
    - { i: 'images:/oracle/7/amd64',       alias: 'oracle-7' }

lxd_preconfigure: 
  - { guest: 'demo-ubuntu-12', template: 'ubuntu-12.04' }
  - { guest: 'demo-ubuntu-14', template: 'ubuntu-14.04' }
  - { guest: 'demo-ubuntu-16', template: 'ubuntu-16.04' }
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: lxd }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
