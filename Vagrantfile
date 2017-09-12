# -*- mode: ruby -*-
# vi: set ft=ruby :

# noinspection RubyResolve
Vagrant.configure('2') do |config|
  # config.vm.box = 'box-cutter/ubuntu1604-desktop' # garbage completely? can't even open a terminal on the desktop
  # config.vm.box = 'bstoots/xubuntu-16.04-desktop-amd64'
  config.vm.box = 'pantsco/crucify'
  config.vm.box_url = '../boxcutter-ubu/box/virtualbox/ubuntu1604-desktop-2017.0.0.box'
  config.vm.hostname = 'butchery'
  # config.vm.network 'private_network', ip: '192.168.42.2' # this works, but doesn't allow WAN access
  # config.vm.network 'public_network'
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
                      path: 'oh-my-zsh-install.sh'

  config.vm.provision :shell, privileged: false,
                      inline: <<-SHELL
    # The automatic rename function is turned on. Add the following to your .tmux.conf 
    # file (and/or run from the command line to have it take effect immediately):
    # set-window-option -g automatic-rename off
    echo 'tits!!!'
  SHELL
end
