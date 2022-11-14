# -*- mode: ruby -*-
# vi: set ft=ruby :

NNODES=6

$script = <<-SCRIPT
echo 'ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCopJkwtulL5xF3CwSShq0kQHuGywlJ+YMTT3Poi6ct8syjGGhkF5y0dxG1Yxl1N+e5i66i3jRkbHCD5TMimAuGs679XcTZ3ro/jWkMDUWggi/sw8Mt09UTuowo8f8UHI6QN0a+BIaZChmXyCSV9YGN58Cgiv1cxXK/YJEthkZM4E5ucrJ1ui+NStLQZmUvEIZKAeHi1bkF+wMAOsD4DxL1bL9jJOf212tVWYBKwpw9gmB9vi8nQsIIgweM6eIhVT++ntQfLyxF5qgZinbkEFiWKpWYTV1PxTkM6ZmZZd965+fhTJ74vvvEGt8hFqMqyrVIVEfKzf7Pz7mMvcizKYZxI5X7zuIleunNpbo4QgOHU82JtVA3ucCL8nPlSGpneSkIIdjjalxZnMRQKQ4dviylVY0KEAMgX6JhZgevbRiQ33rDvFekdhXO+vFyq8Jrxgpi3gLvyv4MUryRn4MhFSUwuu8gWVpPM6vVnpW9e97nWZtrI9hyksQbYkSm+SiSUr8= nitram@zendeb' >> /home/vagrant/.ssh/authorized_keys
SCRIPT

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  (0..NNODES - 1).each do |i|
    config.vm.define "elk-ubuntu-#{i}" do |node|
      #node.vm.box = "ubuntu/focal64"
      node.vm.box = "ubuntu/jammy64"
      node.vm.hostname = "elk-ubuntu-#{i}"
      config.vm.provider "virtualbox" do |v|
          v.memory = 4096
          v.cpus = 4
      end
      node.vm.network "private_network", ip: "192.168.56.11#{i}"
      node.vm.provision "shell", inline: $script
      node.vm.provision "shell", inline: "echo hello from node #{i}"
    end
  end
end