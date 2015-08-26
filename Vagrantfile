# coding: utf-8
# -*- mode: ruby -*-
# vi: set ft=ruby :

require "yaml"

Vagrant.require_version '>= 1.5'

Vagrant.configure(2) do |config|

  _conf = YAML.load(
    File.open(
      File.join(File.dirname(__FILE__), 'provision/default.yml'),
      File::RDONLY
    ).read
  )

  if File.exists?(File.join(File.dirname(__FILE__), 'site.yml'))
    _site = YAML.load(
      File.open(
        File.join(File.dirname(__FILE__), 'site.yml'),
        File::RDONLY
      ).read
    )
    _conf.merge!(_site) if _site.is_a?(Hash)
  end
  _conf['mt_src_dir'] = File.basename(_conf['mt_src'], ".*")


  config.vm.box = _conf['vm_box']
  config.ssh.forward_agent = true

  config.vm.box_check_update = true

  config.vm.hostname = _conf['hostname']

  config.vm.network :private_network, ip: _conf['ip']
  # config.vm.network :forwarded_port, guest: 80, host: 80

  config.vm.synced_folder _conf['sync_folder'], _conf['document_root'], create: "true", owner: "www-data", group: "www-data"

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
      mt_home: _conf['mt_home'],
    }
    ansible.playbook = "provision/playbook.yml"
  end
end
