Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |vb|
     vb.memory = "2048"
  end

  config.vm.network "forwarded_port", guest: 2375, host: 2375
  config.vm.network "forwarded_port", guest: 5000, host: 5000

  config.vm.provision "docker" do |d|
    d.run "registry", args: "-p 5000:5000"
    d.pull_images 'alpine'
  end

  config.vm.provision "shell", path: "docker-config.sh"
end