# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|

  config.vm.box = "8210248/ubuntu-server"

  config.vm.box_url = "https://app.vagrantup.com/8210248/boxes/ubuntu-server"


   config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

   config.vm.network "private_network", ip: "192.168.33.10"

   config.vm.synced_folder "C:\\Users\\root\\Desktop\\workflow", "/var/www/"

   config.vm.synced_folder "C:\\Users\\root\\Desktop\\workflow", "/vagrant", disabled: true

   config.vm.provider "virtualbox" do |vb|

     vb.memory = "1024"
   end

   config.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get install -y apache2
     sudo chmod -R 755 /var/www
     sudo chown -R vagrant:root /var/www
     # установка PHP8.2
     sudo add-apt-repository ppa:ondrej/php -y
     sudo apt update
     sudo apt install -y php8.2 php8.2-cli 
     sudo apt install -y php8.2-mbstring
     sudo apt install -y php8.2-imagick
     # подключение php8.2-fpm

     #sudo apt install -y php8.2-fpm
     #sudo reboot
     #sudo a2enmod proxy_fcgi setenvif
     #sudo a2enconf php8.2-fpm
     #systemctl reload apache2

     # установка MYSQL
     sudo apt install -y mysql-server php8.2-mysql
     systemctl reload apache2
   SHELL
end
