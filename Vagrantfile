Vagrant.configure("2") do |config|
  # Recursos da VM
  config.vm.provider "virtualbox" do |vb|
    vb.name = "vagrant_ubuntu20_vm"
    vb.memory = 1024
    vb.cpus = 1
  end

  # Box base
  config.vm.box = "ubuntu/focal64"

  # Nome da máquina
  config.vm.hostname = "vagrant-ubuntu20"

  # Configuração de rede (Bridge)
  config.vm.network "public_network"

  # Sincronização de pastas
  config.vm.synced_folder "./synced_folder", "/home/vagrant/synced"
end
