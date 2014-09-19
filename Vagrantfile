# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
#VAGRANTFILE_API_VERSION = "2"

Vagrant.configure("2") do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.


#Remember to set the env variable to what you are using
#export VAGRANT_DEFAULT_PROVIDER=vmware_fusion
#export VAGRANT_DEFAULT_PROVIDER=vmware_workstation


  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "virl/emptybase"

# The url from where the 'config.vm.box' box will be fetched if it
# doesn't already exist on the user's system.
# May work
# Will work if you pull it locally
  config.vm.box_url = ""

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.

# The below defaults exist so you can have the vmm native client on your machine and
#  simply have it always pointed to localhost 

config.vm.network "forwarded_port", guest: 19399, host: 19399
config.vm.network "forwarded_port", guest: 19400, host: 19400
config.vm.network "forwarded_port", guest: 19401, host: 19401

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

## Uncomment the below for fusion

config.vm.network "private_network", ip: "172.16.1.0", auto_config: false
config.vm.network "private_network", ip: "172.16.2.0", auto_config: false
config.vm.network "private_network", ip: "172.16.3.0", auto_config: false
config.vm.network "private_network", ip: "172.16.10.0", auto_config: false

  # If true, then any SSH connections made will enable agent forwarding.
  # These are both baked into the box so just leave them set
config.ssh.forward_agent = true
# # Default vagrant username is vagrant.  We need it to be virl so
config.ssh.username = 'virl'

# You automatically get a mount from the directory with your vagrant file onto
# /vagrant of the ubuntu node so I dont call it out here.

# I STRONGLY suggest you make your own version of images mount so you only need to
# download them once
#config.vm.synced_folder "/local/copy/images", "/home/virl/images"

# So you only have to download the vmm binaries once
#config.vm.synced_folder "/local/www/download", "/var/www/download"

# If you run the vmmaestro linux desktop you can keep your own copy of your 
# vmm "workspace" locally 
#config.vm.synced_folder "/local/copy/vmmaestro/configs", "/home/virl/vmmaestro"


## The two provider sections below are included automatically in the box...only uncomment
## if/when you need to make changes
config.vm.provider "vmware_fusion" do |v, override|
  v.vmx["ethernet1.connectionType"] = "custom"
  v.vmx["ethernet1.vnet"] = "vmnet2"
  v.vmx["ethernet1.present"] = "TRUE"
  v.vmx["ethernet1.addressType"] = "generated"
  v.vmx["ethernet2.present"] = "TRUE"
  v.vmx["ethernet2.connectionType"] = "custom"
  v.vmx["ethernet2.addressType"] = "generated"
  v.vmx["ethernet2.vnet"] = "vmnet3"
  v.vmx["ethernet3.present"] = "TRUE"
  v.vmx["ethernet3.connectionType"] = "custom"
  v.vmx["ethernet3.addressType"] = "generated"
  v.vmx["ethernet3.vnet"] = "vmnet4"
  v.vmx["ethernet4.present"] = "TRUE"
  v.vmx["ethernet4.connectionType"] = "custom"
  v.vmx["ethernet4.addressType"] = "generated"
  v.vmx["ethernet4.vnet"] = "vmnet5"
  v.vmx["memsize"] = "8096"
  v.vmx["numvcpus"] = "4"
  v.vmx["mks.enable3d"] = "TRUE"
  v.vmx["logging"] = "FALSE"
  v.vmx["MemTrimRate"] = "0"
  v.vmx["MemAllowAutoScaleDown"] = "FALSE"
  v.vmx["mainMem.backing"] = "swap"
  v.vmx["sched.mem.pshare.enable"] = "FALSE"
  v.vmx["snapshot.disabled"] = "TRUE"
  v.vmx["isolation.tools.unity.disable"] = "TRUE"
  v.vmx["unity.allowCompostingInGuest"] = "FALSE"
  v.vmx["unity.enableLaunchMenu"] = "FALSE"
  v.vmx["unity.showBadges"] = "FALSE"
  v.vmx["unity.showBorders"] = "FALSE"
  v.vmx["unity.wasCapable"] = "FALSE"
end

config.vm.provider "vmware_desktop" do |vd, override|
  vd.vmx["ethernet1.connectionType"] = "custom"
  vd.vmx["ethernet1.vnet"] = "vmnet2"
  vd.vmx["ethernet1.addressType"] = "generated"
  vd.vmx["ethernet2.connectionType"] = "custom"
  vd.vmx["ethernet2.addressType"] = "generated"
  vd.vmx["ethernet2.vnet"] = "vmnet3"
  vd.vmx["ethernet3.connectionType"] = "custom"
  vd.vmx["ethernet3.addressType"] = "generated"
  vd.vmx["ethernet3.vnet"] = "vmnet4"
  vd.vmx["ethernet4.connectionType"] = "custom"
  vd.vmx["ethernet4.addressType"] = "generated"
  vd.vmx["ethernet4.vnet"] = "vmnet5"
  vd.vmx["memsize"] = "8096"
  vd.vmx["numvcpus"] = "4"
  vd.vmx["mks.enable3d"] = "TRUE"
  vd.vmx["logging"] = "FALSE"
  vd.vmx["MemTrimRate"] = "0"
  vd.vmx["MemAllowAutoScaleDown"] = "FALSE"
  vd.vmx["mainMem.backing"] = "swap"
  vd.vmx["sched.mem.pshare.enable"] = "FALSE"
  vd.vmx["snapshot.disabled"] = "TRUE"
  vd.vmx["isolation.tools.unity.disable"] = "TRUE"
  vd.vmx["unity.allowCompostingInGuest"] = "FALSE"
  vd.vmx["unity.enableLaunchMenu"] = "FALSE"
  vd.vmx["unity.showBadges"] = "FALSE"
  vd.vmx["unity.showBorders"] = "FALSE"
  vd.vmx["unity.wasCapable"] = "FALSE"
end



#  Boot with graphics enabled..you can easily change true to false and live without
config.vm.provider "vmware_fusion" do |vf|
 vf.gui = true
end

config.vm.provider "vmware_workstation" do |vw|
 vw.gui = true
end


##Provision

#change the below names to your keys
# You do not need this if pointed at open virl server

config.vm.provision :salt do |salt|
  salt.run_highstate = false
  salt.minion_key  = "./example.virl.info.pem"
  salt.minion_pub  = "./example.virl.info.pub"
  salt.minion_config  = "./minion"
end

config.vm.provision :shell, :inline => <<END
#rm /etc/salt/pki/minion/minion_master.pub 2> /dev/null
cp -f /vagrant/virl.ini /etc/virl.ini


# Bring ubuntu up to date
#apt-get -y update -qq
#apt-get -y upgrade

#This builds local salt tree
/usr/local/bin/vinstall salt

#This is where the magic happens  (updated ank,std,vmmaestro)
/usr/local/bin/vinstall fourth


# Your salt-master if external should be set to salt-master.cisco.com 
# or eu-salt-master.cisco.com


# If we end up stripping desktop in the future and want it back
# or addtional binaries you want to install here
#salt-call state.sls desktop -l quiet
#salt-call state.sls vmm-download -l quiet
#salt-call state.sls vmm-local -l quiet

# This will pull all the images but will could take quite a long time
# to run depending on what its downloaded
salt-call state.sls routervms 
#

END

end
