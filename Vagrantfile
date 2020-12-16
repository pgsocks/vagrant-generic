#!/usr/bin/ruby -w

require 'json'
require 'io/console'

json = IO.popen('ansible-inventory --list').read()
project = JSON.parse(json)

Vagrant.configure('2') do |config|

  project['_meta']['hostvars'].each_with_index do |host, index|

    hostvars = host[1]
    hostname = host[0]

    config.vm.define hostname do |node|

      node.vm.hostname = hostname

      node.vm.box = hostvars['vagrant_box']
      if hostvars.has_key?('vagrant_box_url')
        node.vm.box_url = hostvars['vagrant_box_url']
      end

      node.vm.provider :libvirt do |libvirt|
        libvirt.memory = hostvars['vagrant_memory'] ||= 2048
        libvirt.cpus = hostvars['vagrant_cpus'] ||= 2
        libvirt.driver = 'kvm'
      end

    end
  end

end

