# _*_ mode: ruby _*_


VAGRANT_API_VERSION = "2"

Vagrant.configure(VAGRANT_API_VERSION) do |config|
  config.vm.box = "bento/centos-6.7"
  
  config.ssh.insert_key = false

  config.vm.network "forwarded_port", guest: 80, host: 9090
  config.vm.network "forwarded_port", guest: 9000, host: 9000
  config.vm.provision :shell, inline: "cp -f /vagrant/nginx.repo /etc/yum.repos.d/."

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "playbook.yml"
  end


end


