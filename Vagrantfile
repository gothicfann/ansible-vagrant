# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'

current_dir = File.dirname(File.expand_path(__FILE__))
configs = YAML.load_file("#{current_dir}/config.yml")
vagrant_config = configs['configs']

Vagrant.configure("2") do |config|

  config.vm.provider "virtualbox" do |v|
    v.memory = vagrant_config['memory']
    v.cpus = vagrant_config['cpus']
  end

  N = vagrant_config['nodes']
  (1..N).each do |node_id|
    config.vm.define "node#{node_id}" do |node|
      node.vm.hostname = "node#{node_id}"
      node.vm.network "private_network", ip: "192.168.77.#{20+node_id}"
      node.vm.box = vagrant_config['box']

      if node_id == N
        node.vm.provision "ansible" do |ansible|
          ansible.limit = "all"
          ansible.playbook = vagrant_config['playbook']
          ansible.become = true
          ansible.galaxy_roles_path = "roles/"
        end
      end
    end
  end

end
