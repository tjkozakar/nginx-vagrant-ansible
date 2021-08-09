Vagrant.configure("2") do |hello|

  hello.vm.box = "centos/7"

  hello.vm.network "forwarded_port", guest: 22, host: 2226

  hello.vm.network "forwarded_port", guest: 80, host: 8086
  
  hello.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "dockerize-playbook.yml"
  end
end
