# -*- mode: ruby -*-
# vi: set ft=ruby :

# noinspection RubyResolve
Vagrant.configure('2') do |config|
  config.vm.box = 'ubuntu/xenial64'
  config.vm.hostname = 'butchery'
  config.vm.provider 'virtualbox' do |v|
    v.memory = '4096'
    v.cpus = '6'
  end

  # provision using root
  config.vm.provision 'ansible_local' do |ansible|
    ansible.playbook = 'playbook.yml'
  end
  # provision a user (todo fig out the sublime world (probably needs x))
  # config.vm.provision 'ansible_local' do |ansible|
  #   ansible.playbook = 'playbook-user.yml'
  # end
  
  # todo this is garbage.
  # this has hardcoded `ubuntu` user in it
  config.vm.provision :shell, privileged: false,
                      path: 'oh-my-zsh-install.sh'

  config.vm.provision :shell, privileged: false,
                      inline: <<-SHELL
    echo 'tits!!!'
  SHELL
end
