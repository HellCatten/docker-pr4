Vagrant.configure("2") do |config|
  (1..4).each do |i|
    config.vm.define "vm-#{i}" do |node|
      node.vm.box = "ubuntu/jammy64"
      node.vm.hostname = "ubuntu-node-#{i}"

      node.vm.synced_folder "./shared", "/home/vagrant/shared", type: "virtualbox"

      node.vm.provision "file", source: "./provision_test.txt", destination: "/home/vagrant/provision_test.txt"

      node.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.cpus = 1
      end
    end
  end
end