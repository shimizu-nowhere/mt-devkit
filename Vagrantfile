# coding: utf-8
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  _conf = {
    "mt_src" => "MT-6.1.2.zip",
    "hostname" => "mt-devkit.dev",
    "ip" => "192.168.33.185",
    "document_root" => "/var/www/mt-devkit",
    "sync_folder" => "www/mt-devkit",
  }
  _conf['mt_src_dir'] = File.basename(_conf['mt_src'], ".*")

  config.vm.box = "chef/debian-7.8"
  config.ssh.forward_agent = true

  config.vm.box_check_update = true

  config.vm.hostname = _conf['hostname']

  config.vm.network :private_network, ip: _conf['ip']
  # config.vm.network :forwarded_port, guest: 80, host: 80

  config.vm.synced_folder _conf['sync_folder'], _conf['document_root'], :create => "true"

  if Vagrant.has_plugin?('vagrant-hostsupdater')
    config.hostsupdater.remove_on_suspend = true
  end

  if Vagrant.has_plugin?('vagrant-vbguest')
    config.vbguest.auto_update = false
  end

  config.vm.provision "ansible" do |ansible|
    ansible.extra_vars = {
      mt_src: _conf['mt_src'],
      mt_src_dir: _conf['mt_src_dir'],
      hostname: _conf['hostname'],
      document_root: _conf['document_root'],
    }
    ansible.playbook = "playbook.yml"
  end
end
