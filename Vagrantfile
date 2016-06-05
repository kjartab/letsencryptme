
    config.vm.box = "szops/ubuntu-xenial-amd64"
    config.ssh.insert_key = true

    config.vm.provider "virtualbox" do |v|
      v.memory = 8000
      v.cpus = 4
    end

    config.vm.network :forwarded_port, host: 8014, guest: 80 # Apache
    config.vm.network :forwarded_port, host: 3004, guest: 9200 # ElasticSearch

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "provision/playbook.yaml"
        ansible.inventory_path = "provision/test_inventory"
        ansible.verbose = "vvvv"
        ansible.limit = "vagrant"
    end
