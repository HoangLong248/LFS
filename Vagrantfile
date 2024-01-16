Vagrant.configure("2") do |config|
  # Install Vagrant plugins
  # If any of these are missing, they will be automatically installed
  # Then the vagrant command must be repeated
  config.vagrant.plugins = ["vagrant-scp", "vagrant-vbguest", "vagrant-timezone", "vagrant-reload"]

  # Create the VM
  config.vm.define "LFS" do |subconfig|
    subconfig.vm.box = "centos/7"
    subconfig.vbguest.auto_update = true # Requires the vagrant-vbguest plugin
    subconfig.vm.hostname = "LFS-Host"
    # Networking - Uncomment below per your networking requirements
    # For bridged network with VirtualBox, use 'VBoxManage list bridgedifs` to list
    # available NICs suitable for bridging. use the "Name:" field for "bridge:"  
    #subconfig.vm.network "public_network", ip: "172.16.1.150", bridge: "My Ethernet NIC name"
    # subconfig.vm.network "public_network", ip: "172.16.1.150", bridge: "My Wireless NIC name"
    subconfig.vm.network :private_network, ip: "10.0.0.100"
  end

  # Set timezone - requires the vagrant-timezone plugin
  config.timezone.value = "Asia/Ho_Chi_Minh"

  # Virtual machine specs - VirtualBox
  config.vm.provider "virtualbox" do |spec|
    # Show the virtual machine console
    spec.gui = false
    # CUP and RAM
    spec.cpus = 2
    spec.memory = 8192
    # spec.customize ["modifyvm", :id, "--largepages", "on"]
    # # Add a virtual optical drive, allows easy mounting of ISOs
    # spec.customize ["storageattach", :id,
    #         "--storagectl", "IDE",
    #         "--port", "0", "--device", "1",
    #         "--type", "dvddrive",
    #         "--medium", "emptydrive"]
    # # Use Hardware virtualization features
    # spec.customize ["modifyvm", :id, "--hwvirtex", "on"]
    # spec.customize ["modifyvm", :id, "--vtxux", "on"]
    # spec.customize ["modifyvm", :id, "--nested-hw-virt", "off"]
  end

#   # Post-configuration bash script, runs as root after VM creation
#   $post_config = <<-'SCRIPT'
#   # Install EPEL
#   yum -y install epel-release
#   # Update Linux
#   yum -y update
#   # Install and enable Graphical Desktop
#   # echo ""
#   # echo "Installing Gnome Desktop"
#   # echo "------------------------"
#   # yum -y install '@^GNOME Desktop'
#   # systemctl isolate graphical.target
#   # systemctl set-default graphical.target
#   SCRIPT

#   # Run post_config script
#   config.vm.provision "shell", inline: $post_config

  # Reboot - requires the vagrant-reload plugin
  config.vm.provision :reload
end