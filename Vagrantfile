# -*- mode: ruby -*-
# vi: set ft=ruby :

# noinspection RubyResolve
Vagrant.configure('2') do |config|
  config.vm.box = 'boxcutter/ubuntu1604-desktop'
  config.vm.hostname = 'butchery'
  config.vm.provider 'virtualbox' do |v|
    v.memory = '4096'
    v.cpus = '6'
    v.gui = true
  end

  # provision using root
  config.vm.provision 'ansible_local' do |ansible|
    ansible.playbook = 'playbook.yml'
    ansible.install_mode = 'pip'
  end
  config.vm.provision 'ansible_local' do |ansible|
    ansible.playbook = 'playbook-user.yml'
  end

  config.vm.provision :shell, privileged: false,
                      inline: <<-SHELL
    # The automatic rename function is turned on. Add the following to your .tmux.conf 
    # file (and/or run from the command line to have it take effect immediately):
    # set-window-option -g automatic-rename off
    echo 'tits!!!'
  SHELL
end
