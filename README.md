virl-emptybase
==============


Starter files for installing virl through vagrant.

0. Install vagrant and your appropriate key
1. Clone this repo
2. mv Vagrantfile.internal to Vagrantfile if your internal
2. mv Vagrantfile.external to Vagrantfile if your external
3. if external send email to virl-install to request your salt keys.
4. copy keys to this directory.
5. alter Vagrantfile to reflect your key names.
6. in the Examples directory there are a few settings.ini to
    get you going
7. Edit settings.ini to reflect your usecase if needed. Variables to note:
  cml?
  onedev
  inside cisco?
  virl type
8. If your going to be doing dev work please consider mounting from your 
    local filesystem into the examples provided in the Vagrantfile.
    This will keep you from downloaded the router images or VMMaestro 
    binaries again and again.
9. Set your env variable so that vagrant knows NOT to use virtualbox
   export VAGRANT_DEFAULT_PROVIDER=vmware_fusion
   or 
   export VAGRANT_DEFAULT_PROVIDER=vmware_workstation
10. vagrant up   (in the directory containing your Vagrantfile settings.ini
                  and keys)
