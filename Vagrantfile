VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "centos-6.5"

  # The url from where the 'config.vm.box' box will be fetched if it doesn't already exist on the user's system.
  config.vm.box_url = "https://googledrive.com/host/0B2jawpwHVC9xT3JJYlo4RTZaNjQ/centos-6.5-x86_64-v20131202-guest-addition-4.3.4.box"
  
  
  config.vm.network :forwarded_port, guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network :private_network, ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network :public_network

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  config.ssh.forward_agent = true

  config.vm.synced_folder "/data", "/vagrant_data"

  config.vm.provider :virtualbox do |vb|   
     vb.customize ["modifyvm", :id, "--memory", "2048"]
  end  

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"        
  end
   
end
