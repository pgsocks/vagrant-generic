This is a master Vagrantfile for generalizing multi-machine projects by using
host variables in an Ansible inventory to create Vagrant hosts. It only works
for the libvirt provider currently. This is useful for quickly testing Ansible
roles and playbooks.

The idea for this project was inspired by Bert Van Vreckem's [One Vagrantfile
to rule them all][1]

# Dependencies
* Vagrant
* Vagrant Libvirt provider
* Libvirt

# Usage

In the Ansible inventory, add the following to each host's variables. Anything
without a default value is mandatory.

|name|type|description|default|
|:---|:---|:----------|:------|
|`vagrant_box`|String|Name of the Vagrant box||
|`vagrant_box_url`|String|URL of the Vagrant box|`omit`|
|`vagrant_memory`|Integer|Amount of memeory in MiB|`2048`|
|`vagrant_cpus`|Integer|Number of CPUs|`2`|

**NOTE:** If the inventory is not in a standard location, then it will need to
be specified in an `ansible.cfg` file along with the Vagrantfile.

---

With the inventory complete, simply use `vagrant up`.

[1]: https://github.com/bertvv/vagrant-skeleton

