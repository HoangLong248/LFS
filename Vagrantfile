Vagrant.configure("2") do |config|
  # Install Vagrant plugins
  # If any of these are missing, they will be automatically installed
  # Then the vagrant command must be repeated
  config.vagrant.plugins = ["vagrant-scp", "vagrant-vbguest", "vagrant-timezone", "vagrant-reload"]

  # Create the VM
  config.vm.define "LFS" do |subconfig|
    subconfig.vm.box = "bento/rockylinux-8"
    subconfig.vbguest.auto_update = true # Requires the vagrant-vbguest plugin
    subconfig.vm.hostname = "LFS"
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
  # $post_config = <<-'SCRIPT'
  # apt-get install bash-completion
  # SCRIPT

#   # Run post_config script
#   config.vm.provision "shell", inline: $post_config

  # Reboot - requires the vagrant-reload plugin
  config.vm.provision :reload
end