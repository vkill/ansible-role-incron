local_ubuntu_1404_box_file = File.expand_path('../trusty-server-cloudimg-amd64-vagrant-disk1.box', __FILE__)
if File.exists?(local_ubuntu_1404_box_file)
  ubuntu_1404_box_url = local_ubuntu_1404_box_file
else
  ubuntu_1404_box_url = "http://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"
end

local_centos_65_box_file = File.expand_path('../centos65-x86_64-20140116.box', __FILE__)
if File.exists?(local_centos_65_box_file)
  centos_65_box_url = local_centos_65_box_file
else
  centos_65_box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"
end

Vagrant.configure(2) do |config|

  config.vm.define 'Ubuntu_1404' do |os_config|
    os_config.vm.box = "ansible-role-incron_Ubuntu-14.04"
    os_config.vm.box_url = ubuntu_1404_box_url
    os_config.vm.network "public_network"

    os_config.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "2048"
    end

    os_config.vm.provision "ansible" do |ansible|
      ansible.playbook = "vagrant_playbook.yml"
      ansible.verbose = "vvvv"
    end
  end

  config.vm.define 'CentOS_65' do |os_config|
    os_config.vm.box = "ansible-role-incron_CentOS-6.5"
    os_config.vm.box_url = centos_65_box_url
    os_config.vm.network "public_network"

    os_config.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "2048"
    end

    os_config.vm.provision "ansible" do |ansible|
      ansible.playbook = "vagrant_playbook.yml"
      ansible.verbose = "vvvv"
    end
  end

end
