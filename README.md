This is a master Vagrantfile for generalizing multi-machine projects by using
host variables in an Ansible inventory to create Vagrant hosts. It only works
for the libvirt provider currently.

The idea for this project was inspired by Bert Van Vreckem's [One Vagrantfile
to rule them all][1]

# Dependencies
* Vagrant
* Vagrant Libvirt provider
* Libvirt

# Usage

In the Ansible inventory, add the following to each host's variables.

* `vagrant_box`
* `vagrant_box_url` (optional)
* `vagrant_memory` (default 2048MiB)
* `vagrant_cpus` (default 2)

---

With the inventory complete, simply use `vagrant up`.

[1]: https://github.com/bertvv/vagrant-skeleton

