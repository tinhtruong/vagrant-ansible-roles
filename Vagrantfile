VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "centos"

  # The url from where the 'config.vm.box' box will be fetched if it doesn't already exist on the user's system.
  #config.vm.box_url = "http://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.4-x86_64-v20130731.box"
  #config.vm.box_url = "file:///data/vagrant-test/centos-6.4-x86_64-v20131125-guest-addition-v4.3.2.box"
  
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
