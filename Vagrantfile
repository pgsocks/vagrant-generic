#!/usr/bin/ruby -w

require 'yaml'

hosts = YAML.load_file('vagrant_hosts.yml')

Vagrant.configure("2") do |config|

  hosts.each do |host|
    config.vm.define host['name'] do |node|

      node.vm.box = host['box']
      node.vm.hostname = host['name']
      if host.has_key?('box_url')
        node.vm.box_url = host['box_url']
      end

      if host.has_key?('private_networks')
        host['private_networks'].each do |network|
          node.vm.network :private_network, network
        end
      end

      if host.has_key?('public_networks')
        host['private_networks'].each do |network|
          node.vm.network :private_network, network
        end
      end

      node.vm.provider :libvirt do |libvirt|
        libvirt.memory = host['memory'] ||= 2048
        libvirt.cpus = host['cpus'] ||= 2
        libvirt.driver = 'kvm'
      end

    end
  end

end

