# Projeto Vagrant - Ubuntu 20.04

## 📌 Descrição

Este projeto tem como objetivo criar uma máquina virtual utilizando Vagrant com o sistema operacional **Ubuntu 20.04 (focal64)**.

A configuração inclui:

- **Sistema Operacional:** Ubuntu 20.04
- **Memória RAM:** 1 GB
- **CPU:** 1 núcleo
- **Rede:** Modo Bridge (a máquina virtual terá acesso à rede local)
- **Pasta sincronizada:** Para compartilhamento de arquivos entre o Host e a VM


## 🚀 Passos para Subir a Máquina Virtual

1. **Clone o Repositório:**

bash
git clone https://github.com/SEU_USUARIO/vagrant-ubuntu.git
cd vagrant-ubuntu
Inicie a VM com o comando:

bash
vagrant up

O Vagrant irá baixar a box oficial do Ubuntu 20.04 se for a primeira vez que você executa.

Caso a rede peça para selecionar a interface de rede durante o provisionamento, selecione a que representa sua conexão local (exemplo: Wi-Fi ou Ethernet).

## 🔑 Como Acessar a Máquina Virtual via SSH
Após a máquina ser inicializada com sucesso:

bash
vagrant ssh

Com isso, você estará logado dentro da VM.

## 📂 Sincronização de Pastas
Foi configurada uma pasta sincronizada para facilitar o compartilhamento de arquivos entre o host e a VM.

- **Pasta no Host:** ./synced_folder

- **Pasta dentro da VM:** /home/vagrant/synced_folder

**Exemplo de uso:**
No Host:

bash
echo "Arquivo de teste" > synced_folder/teste.txt

Dentro da VM:

bash
cat /home/vagrant/synced_folder/teste.txt

## ⚙️ Conteúdo do Vagrantfile
Abaixo está a configuração utilizada no arquivo Vagrantfile deste projeto:

ruby
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

## ✅ Objetivos Alcançados
 Criação de VM com Ubuntu 20.04

 Definição de recursos: memória e CPU

 Configuração de rede Bridge

 Sincronização de pasta entre host e VM

 Projeto versionado no GitHub