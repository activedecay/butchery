# -*- mode: ruby -*-
# vi: set ft=ruby :

install_libvirt_required = <<-SHELL
  apt install 9mount
SHELL

# The automatic rename function is turned on. Add the following to your .tmux.conf
# file (and/or run from the command line to have it take effect immediately):
# set-window-option -g automatic-rename off
todo = <<-SHELL
    echo 'tits!!!'
SHELL

# noinspection RubyResolve
Vagrant.configure('2') do |config|
  config.vm.hostname = 'butchery'
  config.vm.provider :virtualbox do |v|
    config.vm.box = 'boxcutter/ubuntu1604-desktop'
    v.memory = '4096'
    v.cpus = '6'
    v.gui = true
  end
  config.vm.provider :libvirt do |v|
    config.vm.provision :shell, inline: install_libvirt_required
    config.vm.synced_folder './', '/vagrant',
                            type: '9p',
                            disabled: false,
                            accessmode: 'squash'
    config.vm.box = 'peru/ubuntu-desktop-amd64'
    config.vm.box_version = '20170420.01'
    v.memory = '4096'
    v.cpus = '6'
  end

  # provision using root
  config.vm.provision 'ansible_local' do |ansible|
    ansible.playbook = 'playbook.yml'
    ansible.install_mode = 'pip'
  end
  config.vm.provision 'ansible_local' do |ansible|
    ansible.playbook = 'playbook-user.yml'
  end

  config.vm.provision :shell,
                      privileged: false,
                      inline: todo
end
