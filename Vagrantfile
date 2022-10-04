Vagrant.configure("2") do |config|
  config.vm.box = "almalinux/8"
    config.vm.provision "shell", inline: <<-SHELL
      sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
	  sudo dnf install -y docker-ce docker-ce-cli containerd.io
	  sudo systemctl enable docker.service
	  sudo systemctl start docker.service
	  sudo usermod -aG docker vagrant
    SHELL
end
