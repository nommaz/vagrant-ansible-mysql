# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # set to false, if you do NOT want to check the correct VirtualBox Guest Additions version when booting this box
  if defined?(VagrantVbguest::Middleware)
    config.vbguest.auto_update = true
  end

  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = 'mysql.local'
  config.vm.network :private_network, ip: '192.168.88.12'
  config.vm.network :forwarded_port, guest: 3306, host: 3306
  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"

  config.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--cpus", "1", "--memory", "1024"]
  end

  config.vm.synced_folder "../common", "/common"

  config.vm.provision :shell,
    :keep_color => true,
    :path => "setup.sh"
end
