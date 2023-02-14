Vagrant.configure("2") do |config|

    config.vm.define "master" do |master|
        master.vm.box = "bento/ubuntu-22.04"
        master.vm.network "private_network", ip: "192.168.0.2"
        master.vm.hostname = "master"
        master.vm.provision "shell", path: "docker.sh"
        master.vm.provision "shell", path: "master.sh"
    end

    servers = [
        {
            :hostname => "node1",
            :box => "bento/ubuntu-22.04",
            :ip => "192.168.0.3",
        },
        {
            :hostname => "node2",
            :box => "bento/ubuntu-22.04",
            :ip => "192.168.0.4",
        },
        {
            :hostname => "node3",
            :box => "bento/ubuntu-22.04",
            :ip => "192.168.0.5",
        },
    ]

    servers.each do |machine|
        config.vm.define machine[:hostname] do |node|
            node.vm.box = machine[:box]
            node.vm.hostname = machine[:hostname]
            node.vm.network :private_network, ip: machine[:ip]
            node.vm.provision "shell", path: "docker.sh"
            node.vm.provision "shell", path: "worker.sh"
            
        end
    end

  




end