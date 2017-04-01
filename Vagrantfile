# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['ANSIBLE_ROLES_PATH'] = "../"

Vagrant.configure(2) do |config|

  config.vm.define "localhost" do |localhost|
    localhost.vm.box='ubuntu/xenial64'
    localhost.vm.provider :virtualbox do |v|
      v.name = "localhost"
    end
  end

  config.vm.provision "shell",
    inline: "apt-get install -y python"
  
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "tests/test.yml"
    ansible.sudo = true
    ansible.extra_vars = {
      lxd_preloadimages:
        [ { i: 'images:ubuntu/trusty',  alias: 'ubuntu-14.04' },
          { i: 'images:ubuntu/xenial',  alias: 'ubuntu-16.04' },
          { i: 'images:debian/jessie',  alias: 'debian-8' } ],
      lxd_preconfigure:
        [ { guest: 'demo-ubuntu-14', template: 'ubuntu-14.04' },
          { guest: 'demo-debian-8', template: 'debian-8' } ],
      lxd_zfs_pool_name: 'zpool',
    }
  end
end
