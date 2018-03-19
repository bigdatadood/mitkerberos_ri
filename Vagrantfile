Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = "1024"
    v.cpus = 1
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "70"]
  end
  config.vm.define "mit01" do |mit01|
    mit01.vm.box = "bento/centos-6.7"
    mit01.vm.hostname = "mit01.hdpdev.com"
    mit01.vm.network "private_network", ip: "192.168.60.152"
    mit01.vm.provision "shell", :inline => "sudo echo '192.168.60.159 ambari ambari.hdpdev.com' >> /etc/hosts"
    mit01.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy_mitkerberos.yml"
    end
  end
end
