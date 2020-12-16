This is a master Vagrantfile for generalizing multi-machine projects. It only
works for the libvirt provider currently.

The idea for this project was inspired by Bert Van Vreckem's [One Vagrantfile
to rule them all][1]

# Dependencies
* Vagrant
* Vagrant Libvirt provider
* Libvirt

# Usage
You must provide a file called `vagrant_hosts.yml` alongside the Vagrantfile.
It should contain a list of yaml dictionaries with the following fields.
* `name`
* `box`
* `box_url` (optional)
* `private_networks` (optional)
* `public_networks` (optional)

Private and public networks, if present, should be a list of network options.

---

With `vagrant_hosts.yml` in place, simply use `vagrant up`.

## Example
```yaml
- name: foo
  box: generic/alpine38
- name: bar
  box: generic/alpine38
  private_networks:
    - :libvirt__network_name: net1
- name: bin
  box: generic/alpine38
  private_networks:
    - :libvirt__network_name: net1
    - :libvirt__network_name: net2
```

[1]: https://github.com/bertvv/vagrant-skeleton


