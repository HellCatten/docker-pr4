# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Используем цикл для создания 4 одинаковых машин
  (1..4).each do |i|
    config.vm.define "vm-#{i}" do |node|
      # Базовый образ Ubuntu 22.04
      node.vm.box = "ubuntu/jammy64"
      node.vm.hostname = "ubuntu-node-#{i}"

      # Настройка общей папки (тип virtualbox)
      # "./shared" - папка на хосте (твоем ПК)
      # "/home/vagrant/shared" - папка внутри ВМ
      node.vm.synced_folder "./shared", "/home/vagrant/shared", type: "virtualbox"

      # Провизия: копирование файла
      node.vm.provision "file", source: "./provision_test.txt", destination: "/home/vagrant/provision_test.txt"

      # Настройка провайдера VirtualBox (выделяем по 1 ГБ ОЗУ и 1 ядру процессора)
      node.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.cpus = 1
      end
    end
  end
end