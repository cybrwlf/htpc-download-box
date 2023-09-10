$script = <<-SCRIPT
apt-get update
apt-get install git docker docker-compose -y
systemctl enable docker && systemctl start docker
chown -R vagrant:vagrant /media
git clone https://github.com/cybrwlf/htpc-download-box.git
chown -R vagrant:vagrant htpc-download-box
cd htpc-download-box
cp .env.example .env
docker-compose up -d
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"
  config.vm.provision "shell", inline: $script
  config.vm.network "public_network", ip: "10.0.42.42"
end
