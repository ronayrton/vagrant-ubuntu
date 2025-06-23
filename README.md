# Projeto Vagrant - Ubuntu 20.04

## 📌 Descrição

Este projeto tem como objetivo criar uma máquina virtual utilizando Vagrant com o sistema operacional **Ubuntu 20.04 (focal64)**.

A configuração inclui:

- **Sistema Operacional:** Ubuntu 20.04
- **Memória RAM:** 1 GB
- **CPU:** 1 núcleo
- **Rede:** Modo Bridge (a máquina virtual terá acesso à rede local)
- **Pasta sincronizada:** Para compartilhamento de arquivos entre o Host e a VM

---

## 🚀 Passos para Subir a Máquina Virtual

1. **Clone o Repositório:**

```bash
git clone https://github.com/SEU_USUARIO/vagrant-ubuntu.git
cd vagrant-ubuntu
Inicie a VM com o comando:

bash
Copiar
Editar
vagrant up
O Vagrant irá baixar a box oficial do Ubuntu 20.04 se for a primeira vez que você executa.

Caso a rede peça para selecionar a interface de rede durante o provisionamento, selecione a que representa sua conexão local (exemplo: Wi-Fi ou Ethernet).

🔑 Como Acessar a Máquina Virtual via SSH
Após a máquina ser inicializada com sucesso:

bash
Copiar
Editar
vagrant ssh
Com isso, você estará logado dentro da VM.

📂 Sincronização de Pastas
Foi configurada uma pasta sincronizada para facilitar o compartilhamento de arquivos entre o host e a VM.

Pasta no Host: ./synced_folder

Pasta dentro da VM: /home/vagrant/synced_folder

Exemplo de uso:
No Host:

bash
Copiar
Editar
echo "Arquivo de teste" > synced_folder/teste.txt
Dentro da VM:

bash
Copiar
Editar
cat /home/vagrant/synced_folder/teste.txt
⚙️ Conteúdo do Vagrantfile
Abaixo está a configuração utilizada no arquivo Vagrantfile deste projeto:

ruby
Copiar
Editar
Vagrant.configure("2") do |config|
  # Nome da máquina
  config.vm.define "ubuntu-vm"

  # Box oficial do Ubuntu 20.04
  config.vm.box = "ubuntu/focal64"

  # Configuração de Rede - modo bridge
  config.vm.network "public_network"

  # Pasta sincronizada
  config.vm.synced_folder "./synced_folder", "/home/vagrant/synced_folder"

  # Recursos da VM
  config.vm.provider "virtualbox" do |vb|
    vb.name = "ubuntu-vagrant"
    vb.memory = "1024"
    vb.cpus = 1
  end
end
✅ Objetivos Alcançados
 Criação de VM com Ubuntu 20.04

 Definição de recursos: memória e CPU

 Configuração de rede Bridge

 Sincronização de pasta entre host e VM

 Projeto versionado no GitHub