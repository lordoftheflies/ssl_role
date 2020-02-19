# Ansible Role: SSL

The `ssl_role` setup SSL certificates for inventory.

## Requirements

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

## Role Variables

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Usage

### Example playbooks

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - role: lordoftheflies.ssl_role

## Integration

### For Local Testing

* [Vagrant](https://www.vagrantup.com/) - (Tested using version 2.1.1)
* Vagrant plugins:
  * [vagrant-disksize (0.1.2)](https://github.com/{{ lookup('pipe', 'git config user.name') }}/vagrant-disksize)
  * [vagrant-libvirt](https://github.com/{{ lookup('pipe', 'git config user.name') }}/vagrant-libvirt)
  * vai (0.9.3) - For testing with multiple vms [vagrant-plugin-vai](https://github.com/{{ lookup('pipe', 'git config user.name') }}/vagrant-plugin-vai)
  * [vagrant-vbguest (0.15.2) - Recommended vagrant-vbguest](https://github.com/{{ lookup('pipe', 'git config user.name') }}/vagrant-vbguest)
* [Virtual Box](https://www.virtualbox.org/)
  * Tested using Version 5.2.14 r123301 (Qt5.6.1)

### Set up Molecule environment
```shell script
virtualenv --python=/usr/bin/python3.7 .env
source .env/bin/activate
pip install molecule docker molecule[lint] molecule[docker] molecule[vagrant]
```

### Set up your Molecule scenarios
```shell script
molecule init scenario -s default -d docker -r plantuml_role
molecule init scenario -s lxd -d lxd -r plantuml_role
molecule init scenario -s vagrant -d vagrant -r plantuml_role
```

### Setup Tox
```shell script
pip install tox
```


### Testing

To test with all VM's defined in Vagrantfile run the following:

```shell
vagrant up
```

To run on a specific VM's
```shell
vagrant up xenial
```

### Supported platforms

| OS | Version | Distribution | Supported | Results  |
| :--- | :---: | :---: | :---: | :---: |
| Ubuntu | 19.10 | disco | supported | * |
| Ubuntu | 19.10 | eoan | supported | * |

## License

Apache 2.0

## Author Information

* [László Hegedűs](https://github.com/lordoftheflies) [:envelope:](mailto:laszlo.hegedus@cherubits.hu)
* [Jeff Geerling](https://github.com/geerlingguy) [:envelope:](mailto:laszlo.hegedus@cherubits.hu)
* [Christopher Steel](https://github.com/csteel) [:envelope:](mailto:christopher.steel@mcgill.ca)
> **NOTE**: `ssl_role` generated using `skeleton` from [ansible_role_skeleton](https://github.com/lordoftheflies/ansible_role_skeleton).

#### Referencies

* [Setup certificate-authority](https://networklessons.com/uncategorized/openssl-certification-authority-ca-ubuntu-server)
* [Secure tcp connections](https://docs.docker.com/engine/security/https/)