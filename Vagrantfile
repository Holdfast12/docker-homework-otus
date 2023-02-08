Vagrant.configure("2") do |config|
  config.vm.box = "almalinux/8"
    config.vm.box_check_update = false
    config.vm.network "forwarded_port", guest: 80, host: 80
    config.vm.provision "shell", inline: <<-SHELL
      sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
      sudo dnf install -y epel-release
      sudo dnf install -y docker-ce docker-ce-cli containerd.io screen
      sudo systemctl enable docker.service
      sudo systemctl start docker.service
      sudo usermod -aG docker vagrant
      sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
      sudo chmod +x /usr/local/bin/docker-compose
    SHELL
end
