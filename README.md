virl-emptybase
==============


Starter files for installing virl through vagrant.

0. Install vagrant and your appropriate key
1. Clone this repo

3. if external you will need salt keys.
4. copy keys to cloned directory ./salt
5.
5. alter Vagrantfile to reflect your key names.
7. Edit virl.ini to reflect your use case if needed. Variables to note:
  salt_master, salt_id and salt_domain.
8. To avoid long 'up' times please consider mounting from your
    local filesystem into the examples provided in the Vagrantfile.
    This will keep you from downloading the router images or VMMaestro
    binaries again and again.
9. Set your env variable so that vagrant knows NOT to use virtualbox
   export VAGRANT_DEFAULT_PROVIDER=vmware_fusion
   or
   export VAGRANT_DEFAULT_PROVIDER=vmware_workstation
10. vagrant up   (in the directory containing your Vagrantfile virl.ini
                  and sallt/keys.pem)
