TERRAFORM_DIR = File.expand_path("../terraform")

Vagrant.configure(2) do |config|
	config.vm.define "devops-box" do |devbox|
		devbox.vm.box = "ubuntu/xenial64"
      		devbox.vm.provision "shell", path: "scripts/install.sh"
			if File.directory?(TERRAFORM_DIR)
				devbox.vm.provision "shell", inline: "mkdir -p /home/vagrant/terraform"
				devbox.vm.synced_folder "#{TERRAFORM_DIR}", "/home/vagrant/terraform"
            end
    		devbox.vm.provider "virtualbox" do |v|
    		  v.memory = 4096
    		  v.cpus = 2
    		end
	end
end
