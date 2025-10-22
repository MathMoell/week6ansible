Vagrant.configure("2") do |config|

  # Development server
  config.vm.define "dev" do |dev|
    dev.vm.box = "ubuntu/jammy64"
    dev.vm.hostname = "dev-web"
    dev.vm.network "forwarded_port", guest: 80, host: 8080

    dev.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end

    dev.vm.provision "shell", inline: <<-SHELL
      apt-get update -qq
      apt-get install -y python3
    SHELL
  end

  # Production server
  config.vm.define "prod" do |prod|
    prod.vm.box = "ubuntu/jammy64"
    prod.vm.hostname = "prod-web"
    prod.vm.network "forwarded_port", guest: 80, host: 8081

    prod.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 2
    end

    prod.vm.provision "shell", inline: <<-SHELL
      apt-get update -qq
      apt-get install -y python3
    SHELL
  end
end
