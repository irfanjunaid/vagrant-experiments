web_ram = 1024
web_cpu = 1

db_ram = 1024
db_cpu = 1

Vagrant.configure("2") do |config|

  config.vm.define "web" do |web|
    web.vm.box = "webserver"
    web.vm.network "forwarded_port", guest: 80, host: 8080
    web.vm.provision "shell", path: "provision_web.sh"
    
    web.vm.provider "virtualbox" do |vb|
      vb.memory = web_ram
      vb.cpus = web_cpu
    end
  end

  config.vm.define "db" do |db|
    db.vm.box = "dbserver"
    db.vm.network "forwarded_port", guest: 3306, host: 3307
    db.vm.provision "shell", path: "provision_web.sh"
    
    db.vm.provider "virtualbox" do |vb|
      vb.memory = db_ram
      vb.cpus = db_cpu
    end
  end
end