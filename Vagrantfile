#!/usr/bin/ruby

Vagrant.configure('2') do |config|
  config.vm.box = "ubuntu/xenial64"

  {
    'ubuntu01' => '192.168.33.10',
    'ubuntu02' => '192.168.33.20'
  }.each do |name, address|
    config.vm.define name do |host|
      host.vm.hostname = name
      host.vm.network :private_network, ip: address
    end
  end

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "2", "--ioapic", "on"]
  end

  config.vm.provision 'shell', inline: <<-SCRIPT
    apt-get update
    apt-get -y install python aptitude
  SCRIPT

end
