# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "geerlingguy/ubuntu1604"
    config.vm.network :private_network, ip: "192.168.60.11"
    config.vm.network "forwarded_port", guest: 80, host: 65286
    config.vm.hostname = "drupal.test"
    config.ssh.insert_key = false

    config.vm.provider :virtualbox do |v|
        v.memory = 1024
    end

    # Provisioning configuration for Ansible.
    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbook.yml"
      ansible.config_file = "provisioning/ansible.cfg"
    end
end